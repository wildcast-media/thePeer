# PeerChat

Serverless, end-to-end encrypted chat that runs in any modern browser.

- Two devices connect directly over WebRTC by swapping an invite code and a reply code through any channel.
- On top of WebRTC's own encryption, each chat uses a signed ECDH key exchange and AES-256-GCM with per-direction keys and numbered messages (replays are rejected).
- Each device has an identity key that never leaves it; compare safety numbers to verify a contact.

The whole app is `index.html`. Serve it over HTTPS (for example GitHub Pages) and open it on both devices.

Prototype: not security-audited.
