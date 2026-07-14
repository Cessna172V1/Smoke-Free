# Smoke Free Ledger — standalone app bundle

This folder is a self-contained web app (no build step, no npm install needed).
It's the same tracker you've been using, now set up to run outside Claude and
install like a real app on your phone.

## What's inside
- `index.html` — the entire app: shell + your tracker's full logic and design, all in one file (loads React from a CDN, no bundler required)
- `app.jsx` — a copy of the app code on its own, for easier editing/reference (not loaded directly — `index.html` has it inlined so the app also works when opened straight from your file system, not just when hosted)
- `manifest.json` — makes it installable ("Add to Home Screen")
- `service-worker.js` — lets it work offline once installed
- `icons/` — app icons

Data is saved with the browser's `localStorage`, so it persists between visits
on the same device/browser, same as before.

If you ever want to tweak colours, wording, or the milestone timeline: edit
the code inside `index.html` (between the `<script type="text/babel">` tags).
`app.jsx` is just a plain-text copy for convenience — editing it alone won't
change anything unless you also paste the change into `index.html`.

## Step 1 — Put it online (free, ~5 minutes)
Any static host works. Easiest options:

**GitHub Pages**
1. Create a new GitHub repo, upload all the files in this folder to it.
2. Repo Settings → Pages → Deploy from branch → `main` → `/ (root)`.
3. You'll get a URL like `https://yourname.github.io/smoke-free`.

**Netlify (drag-and-drop, no account needed for a quick test)**
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page.
3. You'll get a live URL instantly.

## Step 2 — Try it as an installed app first
Open the URL on your Android phone in Chrome → menu (⋮) → **"Add to Home
Screen" / "Install app"**. It'll behave like a real app: its own icon, opens
full-screen, works offline. For a lot of people this is all you actually
need — no APK required.

## Step 3 — Turn it into a real .apk (optional)
1. Go to **https://www.pwabuilder.com**
2. Paste your hosted URL in.
3. It scans the site, then click **"Package for stores" → Android**.
4. Download the generated `.apk` (or `.aab` for the Play Store).
5. To install the `.apk` on your phone: transfer it over, tap it, and allow
   "install from unknown sources" if prompted (Android will ask once).

PWABuilder is Microsoft's free, no-code tool for exactly this — it wraps your
installed PWA in a proper signed Android package.

## Notes
- Your existing data won't carry over automatically from the Claude artifact
  version, since that used a different storage system — you'll set your quit
  date once here and it'll take it from there.
