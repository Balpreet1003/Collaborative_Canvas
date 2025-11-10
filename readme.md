# Collaborative Canvas

A lightweight collaborative whiteboard built with a static HTML/CSS/JS frontend and a Node.js + Socket.IO backend. The project is split into two deployable packages so the frontend can live on a static host (e.g. Vercel) while the backend runs on Render or any Node-friendly provider.

## Setup Instructions

The backend provides the Socket.IO hub; the frontend is served as static files.

```bash
# Backend (Socket.IO server)
cd server
npm install
npm start

# Frontend (static assets)
cd frontend
npx serve .
# or python3 -m http.server 4173
```

Before running the frontend, edit `frontend/app-config.js` so `backendUrl` points to your backend URL (for local development use `http://localhost:3000`). Once both services are running, load the address printed by your static server.

## Testing With Multiple Users

1. Start the backend and frontend as described above.
2. Open the frontend URL in your main browser window.
3. Open the same URL in an incognito/private window or a different browser profile.
4. Draw in one window and confirm strokes, cursors, undo/redo, and name updates appear in the other instances in real time.

## Known Limitations / Bugs

- No authentication or access control—anyone with the link can join.
- Collaboration state is in-memory; restarting the backend clears undo/redo history.
- Frontend needs a manual refresh if the backend URL changes (no dynamic discovery).
- Large rooms may strain the single Node process because there is no horizontal scaling yet.

## Time Spent

Approximately 2 days across restructuring, environment setup, documentation, and testing.
