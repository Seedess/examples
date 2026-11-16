# Seedess examples

Two complete samples.

## 1. Client only

A stream already exists — someone created it in the dashboard or a server SDK. The page only
needs the stream id and its public token.

Open [`client-only/index.html`](./client-only/index.html), replace `STREAM` and `TOKEN`, and
serve the folder:

```bash
npx serve examples/client-only
```

It uses hls.js and `https://seedess.com/p2p.js`. No backend, no API key.

## 2. Server creates the stream

The server uses `@seedess/node-sdk` with a secret API key, creates a stream, and serves a
small `/api/seedess` endpoint. The page plays the returned stream through the P2P adapter.

```bash
cd examples/end-to-end
npm install
SEEDESS_API_KEY=key_… npm start
open http://localhost:8787
```

Optional: `SEEDESS_STREAM_URL`, `SEEDESS_STREAM_ID`, `SEEDESS_API_BASE`, `PORT`.

The API key stays in the server process. The browser receives only the public token and the
playback URLs.
