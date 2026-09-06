# Ask about Ammar

A small grounded, tool-using chat agent that answers questions about **Muhammad
Ammar** — AI & software engineer. It's the live demo behind
[muhammadammar324.github.io/Muhammad_Ammar](https://muhammadammar324.github.io/Muhammad_Ammar/)
and also runs standalone at the deployment URL.

## How it works

```
POST /api/chat  { messages: [...] }
        │
        ▼
Vercel Edge Function  (GROQ_API_KEY stays here, never sent to the browser)
        │
        ├─ keyword-retrieve the 4 most relevant chunks from knowledge/*.md
        ├─ Groq chat model (openai/gpt-oss-120b, fallback openai/gpt-oss-20b)
        │     └─ may call the tool:  get_github_repos()  → live api.github.com
        └─ streams NDJSON events: status / grounding / tokens
```

- **Grounding.** The model is given only a short CORE bio, the retrieved context,
  and tool output — and is told to decline when the answer isn't there.
- **Retrieval.** `knowledge/*.md` is bundled into `api/_knowledge.js`
  (`npm run sync`) and split into chunks; a keyword scorer picks the top few per
  question.
- **Tool.** `get_github_repos` hits the public GitHub API live (cached 10 min).

## Layout

| Path | Purpose |
| --- | --- |
| `api/chat.js` | the Edge function — retrieval, tool loop, Groq call |
| `knowledge/*.md` | source of truth for everything the agent may say |
| `api/_knowledge.js` | generated bundle (`npm run sync`) |
| `public/index.html` | standalone chat page served at the deploy root |
| `scripts/bundle.mjs` | regenerates the bundle from `knowledge/` |

## Run locally

```bash
cd agent
npm install -g vercel
cp .env.example .env           # paste a Groq key
npm run sync
vercel dev                     # http://localhost:3000
```

## Deploy

See [`DEPLOY.md`](DEPLOY.md). Hosted free on Vercel; `GROQ_API_KEY` is a Vercel
environment variable.
