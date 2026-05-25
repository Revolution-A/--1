# Password Gate

A minimal password-protected access page. Users enter a numeric code; verification is handled entirely server-side via a Netlify Function — the correct code never reaches the client.

## Tech Stack

- Plain HTML/CSS (no framework)
- Netlify Functions (ESM) for server-side code verification

## Running Locally

```bash
netlify dev
```

The site will be available at `http://localhost:8888`.
