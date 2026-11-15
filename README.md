# Net Chat (P2P)

https://github.com/jamieduk/p2p-chat/

Anonymous, browser-based peer-to-peer chat with file sharing. No accounts or app server required for messages/files — data flows directly between peers over WebRTC data channels.

## Features

- **Create or join sessions** via **6-digit PIN**, **shareable link**, or **QR code**
- **Real-time P2P chat** (WebRTC) with copy-to-clipboard for received messages
- **P2P file transfer**: upload/send files and download received attachments; images show an inline preview
- **Anonymous**: no login; peer IDs are ephemeral
- **Session sharing panel**: PIN, link, and QR available in-chat

## How it works

- **Signaling/broker:** Uses [Trystero](https://github.com/dmotz/trystero) (Nostr strategy over public relays) to exchange WebRTC signaling so peers can discover/connect using a shared room code.
- **Connectivity (ICE):** Configured with public STUN/TURN servers (Google STUN; open TURN relay fallback) to broker NAT traversal for the P2P connection.
- **Transport:** Messages and files are sent peer-to-peer via WebRTC data channels (files chunked).

## Usage

1. Open `index.html` in a modern browser (or serve locally):
   ```bash
   python3 -m http.server 8000
   # then open http://localhost:8000
   ```
2. **Create:** Click *Create P2P Chat Session* and share the PIN/link/QR.
3. **Join:** Enter the 6-digit PIN or open the shared link (`https://jnetai.com/apps/p2p-chat/?code=PIN`).
4. Chat, attach/send files, copy received text, and download attachments.

## Notes

- Requires internet access for signaling relays, ICE (STUN/TURN), and CDN libraries.
- Both peers must keep the tab open during connection and file transfers.
- P2P connectivity depends on network/NAT/firewall conditions; TURN relay improves success but cannot guarantee connectivity in all restricted environments.
- Intended for lightweight anonymous sharing; not audited for high-security or adversarial use cases.
