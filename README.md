# My Remote — consent-based screen sharing

This is a small Node.js web app for **consensual screen sharing**. The recipient must open the invite link, press the share button, and approve the browser's native screen-sharing prompt. The operator can view the shared screen. This starter does **not** provide remote mouse/keyboard control, hidden access, file access, or background installation.

## Run locally
1. Install Node.js 18 or newer.
2. Extract the ZIP and open a terminal in the project folder.
3. Run `npm install`.
4. Run `npm start`.
5. Open `http://localhost:3000`.

Default panel password: `ff505`.

## Change secrets before public deployment
Set environment variables:
- `PANEL_PASSWORD` — a strong, unique panel password.
- `SESSION_SECRET` — a long random secret.
- `NODE_ENV=production` when deployed behind HTTPS.

Example (Linux/macOS):
```bash
PANEL_PASSWORD='replace-this' SESSION_SECRET='replace-with-long-random-secret' NODE_ENV=production npm start
```

## Deployment notes
- Deploy behind HTTPS. Browser screen capture requires a secure context (HTTPS; localhost is allowed for development).
- This starter stores rooms and sessions in memory. Restarting the server clears active rooms.
- For production, add rate limiting, persistent session storage, CSRF protection, a TURN server for networks that block direct WebRTC, and proper authenticated WebSocket session validation.
- Browser support for screen capture varies, especially on mobile. Android browsers may not expose device-wide screen capture. iOS Safari has additional limitations.
- The invite link is a bearer link: anyone who receives it can request to join that session. Share it only with the intended recipient.
