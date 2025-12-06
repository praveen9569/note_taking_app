<h1 align="center">📝 MERN Stack Note Taking App ✨</h1>

![Demo App](/frontend/public/image.png)

Lightweight note-taking app built with the MERN stack (MongoDB, Express, React, Node). This repository contains a simple back-end API and a Vite + React front-end for creating, viewing and deleting notes. The project also includes a rate limiter that integrates with Upstash Redis.

---

## Project structure

- `backend/` — Express API and server code
  - `src/server.js` — main server entry
  - `src/config/db.js` — MongoDB connection
  - `src/config/upstash.js` — Upstash/Redis rate limiter config
  - `src/controllers/notesController.js` — notes CRUD handlers
  - `src/middleware/rateLimiter.js` — rate limiting middleware
  - `src/models/Note.js` — Mongoose model
  - `src/routes/notesRoutes.js` — API routes

- `frontend/` — Vite + React UI
  - `src/main.jsx` — app entry
  - `src/App.jsx` — app shell and routing
  - `src/components/` — UI components
  - `src/pages/` — pages for create/home/detail
  - `src/lib/axios.js` — axios instance used by frontend

---

## Features

- Create, list, view and delete notes
- Simple rate limiting with Upstash Redis (server-side)
- Lightweight Vite React frontend with Tailwind CSS

---

## Requirements

- Node.js (LTS recommended) installed locally
- MongoDB instance (local or hosted)
- (Optional) Upstash Redis credentials if you want to enable the same rate limiting setup

---

## Setup / Run (development)

1. Clone the repository (already in this workspace):

```powershell
git clone <repo-url>
cd mern-thinkboard-master
```

2. Start the backend

```powershell
cd backend
npm install
# set environment variables (see .env.example or below)
npm run dev
```

3. Start the frontend

```powershell
cd frontend
npm install
npm run dev
```

Open the frontend URL reported by Vite (usually `http://localhost:5173`). The backend API runs on the port configured in `backend/src/server.js` (commonly `5000`).

---

## Environment variables

Create a `.env` file in `backend/` and set the following values (example names):

- `MONGO_URI` — MongoDB connection string
- `PORT` — optional server port (default 5000)
- `UPSTASH_REDIS_REST_URL` — Upstash REST URL (if using Upstash)
- `UPSTASH_REDIS_REST_TOKEN` — Upstash token (if using Upstash)

If you don't provide Upstash variables the rate limiter will fall back to an in-memory or default behavior (see `src/middleware/rateLimiter.js`).

---

## API endpoints

- `GET /api/notes` — list notes
- `POST /api/notes` — create a note (body: `{ title, content }`)
- `GET /api/notes/:id` — get note details
- `DELETE /api/notes/:id` — delete a note

Refer to `backend/src/routes/notesRoutes.js` and `backend/src/controllers/notesController.js` for details.

---

## Scripts

- Backend: `npm run dev` (uses nodemon / development server)
- Frontend: `npm run dev` (Vite dev server)

Check each `package.json` in `backend/` and `frontend/` for full scripts.

---

## Contributing

Contributions welcome. Suggested workflow:

1. Fork the repo
2. Create a feature branch
3. Open a pull request with a clear description

Please follow existing code style and keep changes focused.

---

## License

This project does not include a license file in the workspace. Add a `LICENSE` if you want to define terms (for example, MIT).

---

## Contact / Notes

If you want me to update this README further (add screenshots, API examples, or CI/deployment instructions), tell me what you want included and I’ll add it.
