# Deploying the agent to Vercel

Free. ~5 minutes. The Groq key is a server-side environment variable — it never
reaches the browser and is never committed to git.

## Option A — Vercel dashboard (no CLI)

1. Push this repo to GitHub (done).
2. Go to <https://vercel.com/new> and **Import** `MuhammadAmmar324/Muhammad_Ammar`.
3. **Root Directory:** set it to `agent`.
4. **Environment Variables:** add `GROQ_API_KEY` = a key from
   <https://console.groq.com/keys>.
5. **Deploy.**
6. Note the production URL (e.g. `https://muhammad-ammar.vercel.app`). Its
   `/api/chat` is the endpoint.

## Option B — Vercel CLI

```bash
npm i -g vercel
cd agent
vercel                       # link / create the project
vercel env add GROQ_API_KEY  # paste the key, choose Production
vercel --prod
```

## After deploying

In the portfolio's `index.html`, set the endpoint near the bottom of the script:

```js
const AGENT_API = 'https://<your-vercel-url>/api/chat';
```

Commit and push — the chat widget goes live immediately.

## Updating what the agent knows

Edit `knowledge/*.md` → `npm run sync` → commit/push (Vercel redeploys on push).
