# scrobbld

Self-hosted Last.fm analytics dashboard with desktop mode, metadata enrichment, yearly wrapped, and bilingual UI (EN/DE).

## What it does

- Always-visible dashboard navbar with period switcher (last week, 7/30/90/365 days, all time, specific years)
- Fast dashboard analytics: top artists/albums/tracks, recent tracks, heatmap, listening clock, decade chart, top tags
- Library with search + detail pages for artists, albums, and tracks
- Wrapped experience with animated slides and downloadable story PNG
- Settings page for:
  - Last.fm connection + disconnect
  - API key / shared secret management
  - Sync scheduler + manual sync actions
  - Metadata refresh actions
  - Language selection (English/German)
  - App update checks (desktop)
  - Full app reset (delete local user data + scrobbles)
- Desktop app (Electron) with custom titlebar controls

## Stack

- Backend: Node.js, Express, SQLite (`better-sqlite3`)
- Frontend: Vanilla JS, HTML/CSS, Chart.js
- Integrations: Last.fm API, MusicBrainz, local metadata/tag scripts
- Desktop: Electron

## Requirements

- Node.js `>=18 <23` (recommended: Node 20/22 LTS)
- Last.fm account
- Last.fm API credentials

## Quick start (web)

1. Install dependencies

```bash
npm install
```

2. Create environment file

```bash
cp .env.example .env
```

3. Configure `.env`

```env
LASTFM_API_KEY=your_lastfm_api_key_here
LASTFM_USERNAME=your_lastfm_username_here
LASTFM_SHARED_SECRET=your_lastfm_shared_secret_here
OAUTH_CALLBACK_URL=http://localhost:1533/callback
PORT=1533
```

4. Start server

```bash
npm start
```

5. Open

`http://localhost:1533`

## Desktop app

Start Electron app (starts local backend and app window):

```bash
npm run start:desktop
```

Development desktop mode:

```bash
npm run dev:desktop
```

## Docker

```bash
docker-compose up -d
```

Alternative port mapping config is available via `docker-compose.port3000.yml`.

## NPM scripts

- `npm start` - start API/server
- `npm run dev` - watch mode for server
- `npm run start:desktop` - start Electron desktop app
- `npm run dev:desktop` - desktop dev mode
- `npm run fetch-mbid` - enrich artists with MusicBrainz IDs
- `npm run fetch-artist-tags` - fetch/refresh artist tags
- `npm run lastfm-fallback` - fetch fallback images from Last.fm

## Localization

- Supported locales: `en`, `de`
- Default locale: `en`
- Locale files live in `public/locales/`

## Sync and metadata notes

- Initial sync can take a while for large libraries.
- Metadata actions can run for several minutes.
- Top tags / decade quality improves after metadata + tag enrichment jobs complete.

## Updates (desktop)

- On app start, desktop checks for updates and only notifies when a newer version exists.
- Manual check is available in Settings.
- If you see `GitHub API returned 404`, no published release is available yet for the configured repo endpoint.

## Data and reset behavior

- Local data is stored in SQLite (`data/scrobbld.db`).
- "Reset App & Logout" deletes local user data and scrobbles, clears app cache state, and disconnects Last.fm.

## Project structure

```text
scrobbld/
├── public/
│   ├── index.html
│   ├── components/
│   ├── css/
│   ├── js/
│   └── locales/
├── src/
│   ├── api.js
│   └── db.js
├── scripts/
├── electron/
├── data/
├── Dockerfile
├── docker-compose.yml
└── package.json
```

## License

MIT
