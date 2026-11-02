# Follow Me

Share your live location with a link. Press **Start Sharing**, send the link, and anyone with it watches your dot move live on a map until you press **Stop**. No route, no stops, no accounts for watchers.

- `index.html` — home / landing page (home v1.1)
- `tracker.html` — the tracker web app (web v1.1): identity + anonymous sign-in, GPS, sharing engine, diagnostics, on-device logs
- `follow.html?s=<shareId>` — the follower page (v1.1): live mirror via SSE, presence heartbeat, Maintenance section

## How it works

One Firebase Realtime Database record per install is the only source of truth (`live/<shareId>`), written by the owner-authenticated tracker (PATCH position updates + pushed trail points) and streamed to followers over SSE. The share ID is a 128-bit random value in the link — read access only; writes require the install's anonymous-auth owner credential, which never leaves the phone. Database rules, the full design, and every decision live in the project proposal (not in this repo).

## Versions

Each component versions separately: tracker web, follower, home, and (later) Android / iOS. The share link is never versioned.
