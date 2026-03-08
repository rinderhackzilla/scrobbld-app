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

## Stack

- Backend: Node.js, Express, SQLite (`better-sqlite3`)
- Frontend: Vanilla JS, HTML/CSS, Chart.js
- Integrations: Last.fm API, MusicBrainz, local metadata/tag scripts
- Desktop: Electron

## Requirements

- Last.fm account
- Last.fm API credentials

## Localization

- Supported locales: `en`, `de`
- Default locale: `en`

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

## Where are ythe source files?

I'm really lazy and I'll probably not upload the source files in the near future until everything is actually the way I want it.
