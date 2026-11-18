# The Peer

Private, end-to-end encrypted chat that runs in any modern browser. No account, no phone number, no password, and no server that stores or forwards your messages.

## How to use it
1. Open the app and pick a name.
2. Tap **Invite a friend** and send them the link, or let them scan the QR code.
3. Your friend taps the link, picks a name, and you're connected.
4. After that, your friend stays in **Your chats**: tap them to reconnect any time you're both online.

## How it works
- **Finding each other:** every pair of friends shares a random secret. It starts in the invite link's `#fragment`, which browsers never send to the web host. Both devices derive a topic and an encryption key from it and use free public MQTT relays only to announce "I'm here" and to swap WebRTC connection details. The relays see only encrypted data.
- **One-time links:** after the first connection, both devices move to a new private room derived from their key exchange, so a used invite link stops working.
- **Messages** go directly between the two devices over WebRTC. On top of WebRTC's own encryption, each session does a signed ECDH key exchange and uses AES-256-GCM with per-direction keys and numbered messages (replays are rejected).
- **Identity:** each device has a key that never leaves it. A saved contact must always present the same key, and you can compare safety numbers to verify a contact.

## Limits
- Both people must have the app open at the same time; there is no offline delivery.
- Chat history is not saved.
- Your identity and contacts live in this browser. Clearing site data removes them.
- Prototype: not security-audited.

The app is `index.html` plus `qrcode.js` (QR Code Generator by Kazuhiko Arase, MIT license). Serve them over HTTPS, for example with GitHub Pages.
