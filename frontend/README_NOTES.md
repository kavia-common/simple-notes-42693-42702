# Ocean Notes (Astro)

A simple, modern note-taking app built with Astro. It provides a responsive single-page experience with:
- Sidebar listing of notes with search
- Main editor area with auto-save
- Create, edit, and delete (with confirmation)
- LocalStorage persistence by default
- Optional REST backend auto-detection via PUBLIC_API_BASE or PUBLIC_BACKEND_URL

## Getting Started

- npm install
- npm run dev
- Visit /notes

The root path (/) redirects to /notes.

## Environment Variables

The app respects the following public variables (read-only in client):

- PUBLIC_API_BASE: If provided and reachable, the app performs REST calls:
  - GET    {PUBLIC_API_BASE}/notes
  - GET    {PUBLIC_API_BASE}/notes/:id
  - POST   {PUBLIC_API_BASE}/notes
  - PUT    {PUBLIC_API_BASE}/notes/:id
  - DELETE {PUBLIC_API_BASE}/notes/:id
- PUBLIC_BACKEND_URL: Alternative to PUBLIC_API_BASE if that is not set

If neither is set or not reachable at runtime, the app falls back to localStorage.

Other provided envs (from container): PUBLIC_FRONTEND_URL, PUBLIC_WS_URL, PUBLIC_NODE_ENV, PUBLIC_NEXT_TELEMETRY_DISABLED, PUBLIC_ENABLE_SOURCE_MAPS, PUBLIC_PORT, PUBLIC_TRUST_PROXY, PUBLIC_LOG_LEVEL, PUBLIC_HEALTHCHECK_PATH, PUBLIC_FEATURE_FLAGS, PUBLIC_EXPERIMENTS_ENABLED are not required by this app directly.

## Data Model

A Note has:
- id: string
- title: string
- content: string
- createdAt: ISO string
- updatedAt: ISO string

## Accessibility and UX

- Keyboard and screen-reader friendly controls
- Minimalist Ocean Professional theme (blue + amber accents)
- Responsive layout (collapses sidebar above 900px breakpoint)

## Development Notes

- Components are Astro islands composed on a simple SPA-style page.
- Storage selection is dynamic via getAPI() in src/lib/storage.ts.
- LocalStorage uses a seed dataset for first-time users.

## License

MIT
