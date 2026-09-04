# SabiSite

Pitch/landing page + deal tracker for an AI-built website service for Nigerian businesses.

This is a **static site** — plain HTML, CSS, and JavaScript. No framework, no build step,
no bundler. That means it runs anywhere a browser can load an HTML file, and deploys
in seconds to any static host.

## Project structure

```
sabisite-project/
├── index.html       # Main pitch/landing page (SabiSite)
├── tracker.html      # Lead & revenue tracker (uses browser-side persistent storage)
├── package.json      # Optional — only used for a local dev server, not required to run the site
├── netlify.toml       # Netlify deploy config (optional, only needed for CLI/Git-based deploy)
└── README.md
```

## Requirements

- A modern web browser (Chrome, Safari, Firefox, Edge)
- Node.js (only needed if you want to run a local dev server via `npm` — optional)

No other dependencies. There is nothing to `npm install` for the site itself to work.

## Run it locally

**Option A — just open the file (fastest):**

Double-click `index.html`, or open it directly in your browser:

```
open index.html        # macOS
start index.html        # Windows
xdg-open index.html      # Linux
```

**Option B — run a local dev server (recommended if testing on mobile/other devices on your network):**

```bash
npm install
npm run dev
```

This starts a local static server (via the `serve` package) at `http://localhost:3000`.
No build step is required — `serve` just serves the files as-is.

## Build for production

There is no build step. `index.html` and `tracker.html` are already production-ready,
static, and self-contained (all CSS and JS are inline in each file — no external files to bundle).

## Deploy

### Option A — Netlify (drag and drop, no CLI needed)

1. Go to [netlify.com](https://netlify.com) and sign up (free, no card required)
2. Click **"Add new site" → "Deploy manually"**
3. Drag the entire `sabisite-project` folder (or just `index.html`) into the upload box
4. Netlify gives you a live URL instantly, e.g. `https://your-site-name.netlify.app`
5. Optional: rename it under **Site settings → Change site name**

### Option B — Netlify CLI

```bash
npm install -g netlify-cli
netlify deploy --prod --dir=.
```

### Option C — Vercel

```bash
npm install -g vercel
vercel --prod
```

### Option D — Any static host (GitHub Pages, Cloudflare Pages, S3, etc.)

Just upload `index.html` and `tracker.html` — there's nothing else required.

## Notes

- **WhatsApp integration:** All contact buttons link to `https://wa.me/2347047426376` with a
  pre-filled message. To change the number, find-and-replace `2347047426376` across `index.html`.
- **Tracker persistence:** `tracker.html` uses the Claude Artifacts `window.storage` API for
  saving leads and daily outreach counts. This only works when the file is opened inside a
  Claude.ai artifact — if you deploy `tracker.html` standalone (e.g. on Netlify), the storage
  calls will fail since `window.storage` won't exist outside that environment. For a standalone
  deployed version of the tracker, the storage logic would need to be swapped for a real backend
  (e.g. Firebase, Supabase, or a simple database-backed API) — let me know if you want that built.
- **Recent work section:** Update the portfolio cards in `index.html` (search for `portfolio-card`)
  as you complete more real client projects, replacing mockups/links with actual case studies.
