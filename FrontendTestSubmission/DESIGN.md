# Design Document

## Architecture
- React (TypeScript) + React Router.
- Material UI for responsive UI.
- LocalStorage for persistence of shortened URLs and statistics.
- Logging Middleware (`src/api/log.ts`) for sending logs to `/logs` API.

## Pages
- `/` → Shortener page (create up to 5 links, default validity 30 min, optional shortcode).
- `/:code` → Redirect page (validates expiry, records click, redirects to original URL).
- `/stats` → Statistics page (lists URLs, creation/expiry, clicks with details).

## Data Model
```ts
ShortLink {
  code: string
  url: string
  createdAt: number
  expiresAt: number
  clicks: Click[]
}

Click {
  ts: number
  source: string
  lat?: number
  lon?: number
}
