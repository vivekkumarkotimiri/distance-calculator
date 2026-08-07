# Odo Log — deployment guide

This folder is a complete, installable web app (PWA). No build step, no server code — just static files.

## Files
- `index.html` — the app itself
- `manifest.json` — tells the phone this is an installable app
- `sw.js` — service worker, caches the app so it works offline after first load
- `icon-192.png`, `icon-512.png` — app icons

## Deploy (pick one, both are free)

### Option 1: Netlify (easiest)
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page
3. Netlify gives you a live URL immediately (e.g. `https://your-app.netlify.app`)

### Option 2: GitHub Pages
1. Create a new GitHub repo, upload these files to it
2. Go to the repo's **Settings → Pages**
3. Set source to the `main` branch, root folder
4. Your app will be live at `https://yourusername.github.io/your-repo-name`

## Install on your phone
1. Open the live URL in Chrome (Android) or Safari (iPhone)
2. Android/Chrome: tap the **⋮ menu → Add to Home screen / Install app**
3. iPhone/Safari: tap the **Share icon → Add to Home Screen**
4. The app icon appears on your home screen and opens full-screen, like a native app

## About your data
- Everything (readings, settings, vehicle details) is stored in the browser's local storage **on that phone only**. Nothing is uploaded anywhere.
- Use the **Export backup** button in Settings regularly to save a `.json` copy of your data somewhere safe (email it to yourself, save to Drive, etc.)
- If you ever clear your browser's site data, uninstall the app, or switch phones, use **Import backup** to restore from that file.

## Updating the app after deployment
The service worker now checks the network for a fresh copy of the page every time you open the app, and falls back to the offline cache only if there's no connection. That means:
- Just push your changes to `index.html` (or any file) as normal — **no need to manually edit `sw.js` or bump a version number anymore.**
- Open the app while you have internet at least once after deploying, and it'll auto-update and reload itself with the new version.
- It still works fully offline after that first check, using whatever it last successfully loaded.

