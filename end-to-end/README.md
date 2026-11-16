# Seedess examples

Two complete, runnable samples:

- **[`client-only/`](./client-only)** — one HTML page, hls.js + `https://seedess.com/p2p.js`,
  a stream id and a public token. No backend.
- **[`end-to-end/`](./end-to-end)** — a Node server using `@seedess/node-sdk` creates the stream
  and hands the page the playback URLs.

## Client only

```bash
npx serve client-only
```

Replace `STREAM` and `TOKEN` in `client-only/index.html`.

## End to end

```bash
cd end-to-end
npm install
SEEDESS_API_KEY=key_… npm start
open http://localhost:8787
```

## What it shows

```
server (API key) ──createStream──▶ Seedess API
        │                               │
        │                        stream + pk_
        ▼                               ▼
   /api/seedess ───────────────▶ browser page
                                        │
                              hls.js + p2p.js ──▶ peers share segments
```

The API key never leaves the server. The page uses only the per-stream public token.

Docs: https://seedess.com/docs/ · Libraries: https://seedess.com/docs/libraries/
