# Three.js Bookshelf Portfolio — Build Notes

Date: 2026-08-29
Subject: Muhammad Ammar

## What this is

`index.html` is a complete Three.js (r165) experience: an interactive editorial
bookshelf where each of seven "volumes" is a facet of Ammar's work. It is
adapted from the ThreeUI `complete-shelf-landing-page` canonical source
(`complete-shelf-v2.html`, revision `606f200fed86`). The authored engine —
procedural cloth / foil / cover / paper textures, rounded-box book geometry,
page-turn interaction, wood shelf, room, lighting, dust, OrbitControls, the
responsive editorial UI, the reduced-motion path and the no-WebGL static
catalogue — is kept intact. Only content was replaced.

## Changes from the source

- **`BOOKS[]` rewritten** to seven portfolio volumes (per-slot colour,
  palette, geometry and seed kept from the original for visual variety):
  I Profile & education · II Med-GReF (independent research) ·
  III Systems Limited (AI internship) · IV Control Console (final-year project
  with SUPARCO) · V Text-to-SQL · VI AI Tour Booking · VII Sales Forecast.
- Detail-panel meta labels relabelled Binding/Format/Theme/Motif →
  Focus/Period/Stack/Method; field values carry résumé content.
- Editorial masthead, `<title>`, meta description, static-catalogue grid,
  loading copy and in-engine brand literals rebranded to Muhammad Ammar.
- Masthead links added: Résumé (`updated_resume.pdf`), Email, LinkedIn
  (`linkedin.com/in/muhammad-ammar-0483b9276`, from the CV). Static footer
  also links the Control Console GitHub repo.
- Tool-specific cover-art atlas (`COVER_ATLAS_DATA`) dropped and the atlas
  decode path forced off, so covers render from the procedural path; the
  procedural cover's centred title text is removed because the foil layer
  already stamps the title. File drops from ~900 KB to ~315 KB.
- No mention of any conference or paper submission anywhere (Med-GReF is
  presented as independent research).

## Content source

All copy is drawn from `updated_resume.pdf` plus the prior site's Med-GReF
metrics (accuracy 0.82→0.91, ROC-AUC 0.57→0.88, ~2.4× fewer unsupported
findings, 13,216 vetted PMC figures).

## Regenerating

The transform lives in the session scratchpad (`build.py`); it reads
`complete-shelf-v2.html` and writes `index.html`. `claymorphism.html` is the
previous static claymorphic version, kept for reference.

## Verified (Playwright, Chromium)

Desktop 1440 + mobile 390: shelf renders, wheel/arrow/marker navigation,
detail panel per volume, book open + page turn across all five spreads, no
console errors (bar a favicon 404). Content matches the CV; grep for
`NeurIPS|Working Volumes` is clean.
