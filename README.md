# FreeCall signaling on Cloudflare Workers

Single-file Worker (`worker.js`, generated, no dependencies) + one SQLite-backed Durable Object.
Free plan, no credit card, permanent `https://freecall-signaling.<your-subdomain>.workers.dev` address.

* Firebase ID tokens are verified with Google's public keys. No service-account key is needed or stored.
* The directory (names, public identity keys, block lists) is persisted in the Durable Object's storage.
* No FCM wake-up push (needs a service account): the app must be open on both phones to place/receive calls.
* Optional settings (Worker -> Settings -> Variables and Secrets): `TURN_URLS`, `TURN_SECRET` (secret), `STUN_URLS`.
* Edit `FIREBASE_PROJECT_ID` in `wrangler.jsonc` if your Firebase project id is not `freecall-test`.
* Health check: `GET /healthz` -> `{"ok":true}`.

Rebuild `worker.js` from the sources with `python3 server-cloudflare/build.py` in the FreeCall project.
