# Questions Paper Maker

A single-page MCQ & Creative Question (CQ) exam paper builder for Bengali-medium papers, with print-ready PDF output and an answer key. Works fully offline once loaded — everything (state, drafts) is stored in the browser's `localStorage`, no backend required.

## Files

All files are flat — no subfolders needed. Upload every file below into your repo root as-is:

```
index.html            The entire app (HTML + CSS + JS in one file)
manifest.json          PWA manifest — lets the app be "installed" on desktop/mobile
service-worker.js      Offline caching for the app shell
favicon-16.png
favicon-32.png         Browser tab icons
icon-192.png
icon-512.png            PWA install icons
apple-touch-icon.png    iOS home-screen icon
.nojekyll               Tells GitHub Pages not to run Jekyll on these files
```

## Deploy on GitHub Pages

1. Create a new repository on GitHub (e.g. `questions-paper-maker`).
2. Upload every file above directly into the repository root — no folders to create. Easiest way:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-repo>.git
   git push -u origin main
   ```
   (Or just drag-and-drop all the files into the GitHub web UI's "Add file → Upload files" — no subfolders needed.)
3. In the repo, go to **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**.
5. Under **Branch**, choose `main` and folder `/ (root)`, then **Save**.
6. Wait a minute, then your app will be live at:
   ```
   https://<your-username>.github.io/<your-repo>/
   ```

No build step, no dependencies to install — it's static files only.

## Notes

- The app auto-saves your draft to the browser's `localStorage` as you type. This is per-browser/per-device, not synced anywhere.
- The Bengali fonts (Noto Sans/Serif Bengali) load from Google Fonts over the network the first time; after that they're cached by the browser.
- The service worker caches the app shell so it keeps working with no internet connection after the first visit (fonts already cached by then will still render; a first-ever offline visit before any online visit won't have fonts).
- To update the deployed app later, just edit `index.html` (or the other files) and push again — GitHub Pages redeploys automatically within a minute or two. If you change `index.html`, bump `CACHE_NAME` in `service-worker.js` (e.g. `qp-maker-v2`) so returning visitors get the new version instead of a stale cached copy.
