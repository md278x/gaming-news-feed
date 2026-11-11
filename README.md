# gaming-news-feed

News feed for **md278x's personal gaming dashboard** (a single offline HTML file with
Wallcrasher / Nikke / Crystallization Catalyst timers). The dashboard fetches
`https://md278x.github.io/gaming-news-feed/news.json` on load and every 30 minutes and shows
the headlines in a scrolling ticker plus an event countdown strip. If the fetch fails it uses
the last good copy cached in the browser, or the copy built into the dashboard.

Covered games: **GODDESS OF VICTORY: NIKKE** (`"nikke"`) and **The First Descendant** (`"tfd"`).

## Files

| File | Purpose |
| --- | --- |
| `news.json` | The feed the dashboard reads |
| `index.html` | GitHub Pages landing page that renders the same feed in a readable list |
| `README.md` | This file |

## `news.json` schema

```json
{
  "updated": "2026-11-11T03:57:00Z",
  "items": [
    { "game": "nikke", "title": "…", "summary": "short one line", "url": "https://source", "date": "2026-11-12T03:00:00Z" }
  ],
  "countdowns": [
    { "game": "tfd", "label": "TFD Dev Live", "target": "2026-11-16T02:00:00Z", "url": "https://source" }
  ]
}
```

- All times are **UTC ISO 8601** (`…Z`). `date` may be `null` when no exact time was announced.
- `countdowns` only lists future events with an officially announced exact time.
- Every entry links to the official or reputable source it came from; no guessed dates.

## Publishing

Enable GitHub Pages for this repo (Settings → Pages → Deploy from branch → `main` / root).
The feed is then served at `https://md278x.github.io/gaming-news-feed/news.json`, which
allows cross-origin requests, so the dashboard can read it even when opened from a local file.
