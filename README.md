# listening-with

a "spotify jam" solution for youtube music--a host installs the app to start a shared queue that friends can add songs, playlists, and albums to via a web app in the browser.

## tech stack

+ **server** — bun + typescript, websocket-based
+ **web client** — astro 5 + react 19 + tailwind css 4
+ **host app** — kotlin + jetpack compose, plays songs on youtube music via mediasessionmanager

## features

+ real-time queue updates over websockets
+ two-layer queue (songs added individually play first, queued albums/playlists play after the song queue is exhausted)
+ search songs, playlists, and albums in website
+ add entire playlists/albums with optional shuffle
+ join via nfc tap, qr code, or room code
+ display names on song submissions
+ auto-reconnect on connection loss

## running it

### server

```bash
cd server
bun install
bun run index.ts
```

env vars:
+ `PORT` — server port
+ `BASE_URL` — base url for qr codes to point ti

### web client

```bash
cd web-client
bun install
bun run dev
```

dev server runs at localhost:4321. connects to the server at `ws://localhost:2946/ws` in development.

### host app

install `host-app` to your android phone. requires permissions to monitor youtube music playback and play new songs even when app is minimized/phone is asleep.
