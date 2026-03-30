# Client (React + Vite)

Frontend SPA for the Level 4 Todo + Tags app with JWT auth and protected routes.

## Live Links
- CloudFront URL: `https://d2vny3lui91j4l.cloudfront.net`
- API URL used by frontend: `https://level4-capstone-todo-server.onrender.com`

## Product Description
This app supports registration/login and a protected todos experience where authenticated users can create, update, filter, and delete todos and tags.

## Architecture Overview
1. React + Vite SPA handles routing and UI state.
2. Auth pages call backend `/auth/register` and `/auth/login`.
3. JWT token is saved in localStorage and attached to protected API requests.
4. Backend persists data to PostgreSQL via Prisma.
5. UI reloads from API data to verify persistence.

## Routes
### Public
- `/login`
- `/register`

### Protected
- `/todos`

## Environment Variables
Create `.env` from `.env.example`.

| Variable | Required | Purpose |
|---|---|---|
| `VITE_API_BASE_URL` | Yes | Base URL for API requests |

Example:

```bash
VITE_API_BASE_URL=https://level4-capstone-todo-server.onrender.com
```

## Local Setup
1. `npm install`
2. Create `.env` from `.env.example`
3. `npm run dev`
4. Open `http://localhost:5173`

## Scripts
- `npm run dev`
- `npm run build`
- `npm run preview`
- `npm run lint`
- `npm test`

## Deployment Notes
- Frontend is deployed with S3 + CloudFront.
- CloudFront should serve `index.html` for SPA deep links (403/404 fallback behavior).
- Set `VITE_API_BASE_URL` to the deployed API URL before building.

## Troubleshooting
- 401 errors: token missing/expired; log in again.
- CORS errors: backend `CORS_ORIGINS` must include this CloudFront domain and localhost.
- API not reached in production: confirm `VITE_API_BASE_URL` was set at build time.
- Blank page on deep refresh: verify CloudFront SPA fallback is configured.
