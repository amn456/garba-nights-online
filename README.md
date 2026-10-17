# Garba Nights Online 🌙🪔

A browser-based 3D Navratri festival prototype built with Three.js, Vite, Socket.IO, Express and SQLite. It includes a shared public world (no manual rooms), a 50-player server cap, procedural characters/environment, desktop and touch movement, synchronized player movement/dances, public filtered text chat, a server-validated Dandiya cosmetic shop with persistent coins/inventory, daily coins, group Garba rewards, and synchronized YouTube embedded playback.

> **Important scope note:** This is a playable Phase 1/2 build with Dandiya and music additions, not a finished commercial game. Characters are procedural placeholders (not rigged production GLB assets). YouTube search requires an API key. Voice chat, durable friend requests, moderation dashboard, full event calendar, dance battles, and production-grade account authentication are not implemented in this build. Do not advertise those as working features yet.

## Requirements

- Node.js 20 or newer (npm included)
- A modern browser with WebGL
- Optional YouTube Data API v3 key for music search

## Run locally

From this folder:

```bash
npm install
cp .env.example server/.env
npm run dev
```

Then open **http://localhost:5173**. The Vite client runs on port 5173 and the Socket.IO server on port 3001. On Windows PowerShell, use `Copy-Item .env.example server/.env` instead of `cp`.

To run only one side:

```bash
npm run dev --workspace garba-nights-online-server
npm run dev --workspace garba-nights-online-client
```

The SQLite database is created automatically at `server/database/garba.sqlite`. Keep this file persistent when deploying the server; it stores player coin balances, daily reward dates, cosmetic inventory, and reward history. Never commit `.env` or API keys.

## Controls

- **WASD** move, **Shift** run, **Space** jump
- Drag the scene to rotate the camera; mouse wheel zooms
- **1–6** emotes/dances, **G** group Garba, **F** funny dance
- **E** near the Dandiya kiosk opens the shop
- **Enter** opens chat; Enter again sends the message
- On touch devices, use the on-screen joystick and buttons

## Dandiya shop

The first guest profile starts with 1,000 coins. Daily reward grants 100 coins once per UTC day. Group Garba rewards 50 coins subject to a five-minute per-player cooldown when at least three players are doing Group Garba near the central dance floor. The server validates purchases and ownership. The catalog prices are:

| Item | Price |
|---|---:|
| Tiranga Dandiya | 500 |
| Rainbow Festival | 1,000 |
| Flower Festival | 1,200 |
| Peacock Heritage | 1,500 |
| Gujarati Mirror | 1,800 |
| Royal Maharaja | 2,000 |
| Neon Night | 2,500 |
| Midnight Royal | 3,000 |
| Festival Fire | 3,500 |
| Legendary Garba | 5,000 |

## YouTube music

The Music button opens YouTube search and an embedded player. Add a key from Google Cloud Console with **YouTube Data API v3** enabled to `server/.env`:

```env
YOUTUBE_API_KEY=your_key_here
```

Restart the server. The current Festival DJ is the first player in the instance; only that player can change the globally synchronized track. If the DJ leaves, the server elects another connected player. The app uses YouTube's official embed; it does not download audio. Browser autoplay restrictions, video embedding restrictions, regional availability and API quota may affect playback/search. Players may need to press play in the embedded YouTube player.

## Test multiplayer

1. Start both services using `npm run dev`.
2. Open the game in two separate browser profiles (or one normal and one private window).
3. Choose different names and press Play in both sessions.
4. Move and dance in one session; check that the other sees the remote character.
5. Send a chat message; confirm it appears in both clients.
6. Walk to the Dandiya kiosk around world coordinates `(36, 32)` and press E.
7. Buy an item and refresh/rejoin; confirm ownership is retained by the guest token in that browser profile.
8. Configure the YouTube key and test music search/playback.
9. Check `http://localhost:3001/health` for online player count and the capacity.

## Security and limitations

- The server checks movement bounds/speed, dance names, chat length/rate, 50-player capacity, cosmetic ownership, and rewards.
- Guest identity is a random browser token hashed server-side; this is not full authentication and should not be treated as account security.
- Chat has basic filtering/rate limits only. It does not replace robust moderation, block/report workflows, or child-safety tooling.
- The initial server broadcasts movement to all clients and is intended for a small 50-player instance. Production deployment should add interest management, monitoring, backups, stronger identity/authentication, rate limits and abuse handling.
- Use HTTPS/WSS in production. Configure `CLIENT_ORIGIN` with the exact frontend origin, comma-separated if needed.

## Festival character & group update
- Traditional character meshes now include layered Kediyu/Chaniya-Choli-inspired panels, mirror-work details, embroidered trim, necklace/earring accents, sash/dupatta edging and anklet-like cuffs. These are procedural meshes and canvas textures (not external photorealistic assets).
- Extra dance emotes: Dandiya, Spin, Bhangra, Namaste, Stomp and Twirl, in addition to the existing Garba/emote set.
- The **Garba Group** panel appears after joining. Create a group, then another player can approach within 14 world units and click **Join Nearby Group**. Groups are limited to 8 players; members can leave at any time. The server owns group membership and updates nearby group availability.
