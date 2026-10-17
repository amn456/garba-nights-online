# Deployment notes

## Frontend

1. Build with `npm run build` from the project root.
2. Publish `client/dist` to a static host that supports SPA/static assets.
3. Set the build-time environment variable `VITE_SERVER_URL` to the public HTTPS/WSS origin of the Node server (for example, `https://api.example.com`).
4. Rebuild after changing `VITE_SERVER_URL`.

## Backend

1. Deploy the `server` workspace on a persistent Node.js host using Node 20+.
2. Install dependencies from the root workspace or run `npm install` at the root before deployment.
3. Start with `npm run start --workspace garba-nights-online-server`.
4. Set `PORT`, `MAX_PLAYERS=50`, `CLIENT_ORIGIN=https://your-frontend.example`, and optionally `YOUTUBE_API_KEY`.
5. Attach persistent storage for `server/database/garba.sqlite`; ephemeral disks can erase player balances/inventory on restart.
6. Allow WebSocket connections and use HTTPS/WSS. If the host terminates TLS, forward requests to the Node service correctly.

## Environment variables

- `PORT`: server port (default 3001)
- `MAX_PLAYERS`: public-world capacity (default 50)
- `CLIENT_ORIGIN`: comma-separated exact allowed browser origins
- `YOUTUBE_API_KEY`: optional YouTube Data API v3 key
- `VITE_SERVER_URL`: client build-time Socket.IO server URL; defaults to `http://localhost:3001`

## Production checklist

- Set strict CORS origins and secrets in the host's secret manager.
- Confirm persistent database storage and backups.
- Enable HTTPS/WSS and test reconnects.
- Monitor CPU, memory, Socket.IO connections, API quota, and database size.
- Load-test before marketing a 50-player event; the configured cap is not a guarantee that every host can sustain 50 players.
- Add production authentication, friend/block/report tools, moderation workflow, and voice SFU before launching those advertised features.
