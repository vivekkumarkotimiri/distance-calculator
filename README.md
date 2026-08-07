# Bike Distance Tracker — deployment guide

This folder is a complete, installable web app (PWA). No build step, no server, no backend service — just static files. **GitHub Pages alone is enough to host it.**

## What's in v2
- Morning/evening odometer tracking with auto-fill (unchanged from before)
- **Multiple bikes** — switch, add, rename, delete profiles from the top bar / Settings
- **Fuel & Mileage** — log fill-ups, auto-calculated km/l, cost tracking
- **Service Reminder** — set a service interval, get a due/overdue badge based on current odometer
- **Insights & records** — longest day, longest streak, this year's total, lifetime total
- **Light/dark theme toggle** (top-right icon)
- **PDF export** — generates a printable summary via your browser's print dialog (Settings → Export PDF summary)
- **Backup export/import** — still there, now includes all bikes

Existing data from the older single-bike version is migrated automatically into a "My Bike" profile the first time this version loads — nothing is lost.

## Files
- `index.html` — the app itself
- `manifest.json` — tells the phone this is an installable app
- `sw.js` — service worker, network-first so updates apply automatically
- `icon-192.png`, `icon-512.png` — app icons

## Deploy on GitHub Pages
1. Push these files to your existing repo (overwrite `index.html`; the others are unchanged)
2. Settings → Pages should already be configured from before — no changes needed there
3. GitHub rebuilds automatically within a minute or two of every push
4. Open the app once with internet after deploying — it self-updates and reloads

## About your data
- Everything (readings, fuel logs, service records, vehicle details, settings) is stored in the browser's local storage **on that phone only**. Nothing is uploaded anywhere.
- Use **Export backup** in Settings regularly to save a `.json` copy of your data somewhere safe.
- If you ever clear your browser's site data, uninstall the app, or switch phones, use **Import backup** to restore from that file.

