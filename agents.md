# AGENTS.md

## Architecture

Single-page static site with one Netlify Function.

```
index.html                   — password form UI
netlify/functions/verify.mjs — server-side code verification
netlify.toml                 — build/function config
```

## Key Decisions

- **No JavaScript verification**: The correct code (`928`) lives only in `verify.mjs`, which runs on Netlify's servers. The browser never receives it, preventing bypass via DevTools.
- **Error signalling via query param**: On a wrong code, the function redirects to `/?error=1`. The page reads this param and renders the Russian error message client-side — keeping the flow a standard form POST/redirect cycle with no JSON API.
- **ESM function format**: `verify.mjs` uses the Netlify Functions v2 ESM format (`export default async (req) => {}`), which is the current recommended approach.

## Coding Conventions

- No build step — the published directory is the repo root (`.`).
- Keep all auth logic inside `netlify/functions/verify.mjs`; do not move it to the frontend.
