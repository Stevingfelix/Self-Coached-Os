# Self-Coached OS — how to install on your phone

The app is now a **Progressive Web App**. To install it on your phone you need to host the files on the web (the service worker won't run from a `file://` path). Three easy options below — pick whichever you like best. All free.

## Files in this folder

- `self-coached-os.html` — the app
- `manifest.json` — PWA manifest (name, icons, theme)
- `sw.js` — service worker (offline cache)
- `icon-192.png` `icon-512.png` `icon-maskable-512.png` — app icons

Upload **all of them** to wherever you host. They must sit in the same folder.

---

## Option 1 — Netlify Drop (easiest, 60 seconds)

1. Go to **https://app.netlify.com/drop**
2. Drag this whole folder onto the page.
3. Netlify gives you a URL like `https://random-name-12345.netlify.app`. Open that URL on your phone.
4. On **Android**: tap the **Install app** button in the header (or use the browser's "Install" prompt). Done.
5. On **iOS**: tap the **Install app** button — it opens a quick how-to: tap Share → Add to Home Screen.

(Optional) Make a free Netlify account and you can rename the URL to anything like `selfcoachedos.netlify.app`.

## Option 2 — Vercel

1. Install the Vercel CLI: `npm i -g vercel`
2. In this folder run: `vercel`
3. Follow the prompts. It deploys and gives you a URL.

## Option 3 — GitHub Pages

1. Create a new public repo on GitHub.
2. Upload these files (or `git push` them).
3. Repo settings → Pages → set branch to `main`, folder `/ (root)`.
4. Visit `https://<username>.github.io/<repo>` on your phone.

## Option 4 — Cloudflare Pages

1. Go to **https://pages.cloudflare.com**
2. Connect to your GitHub repo (free) or use the direct-upload option.
3. Deploy.

---

## Installing on your phone once it's hosted

### Android (Chrome / Edge / Brave)
- Open the URL.
- Tap the **Install app** button in the app's header, OR wait for Chrome's "Install app" prompt at the bottom, OR menu (⋮) → "Install app".
- Icon appears on home screen, opens fullscreen, no browser chrome.

### iPhone / iPad (Safari)
- Open the URL in Safari.
- Tap the **Share** icon at the bottom (square with up-arrow).
- Scroll down, tap **Add to Home Screen** → Add.
- Icon appears on home screen, opens fullscreen.

(The app's **Install app** button on iOS shows these steps in a modal.)

---

## How offline works

Once the service worker registers (first time you load the app online), it caches the HTML, manifest, icons, and Chart.js. After that, the app loads instantly even with no signal — gym basement, plane, anywhere. Your data is in your phone's localStorage so it persists forever. Use Export in the header to back up the JSON.

## Updating to a new version

When you change the HTML, bump the `CACHE` name at the top of `sw.js` (e.g. `sc-os-v1` → `sc-os-v2`). The next time the user opens the app online, the new shell will replace the cached one.

## What you can't do as a PWA (yet)

- **No App Store listing.** For that, wrap with Capacitor (~1–2 days).
- **No iOS push notifications** until users are on iOS 16.4+ and the app is added to the home screen.
- **No HealthKit / Apple Watch.** Native or Capacitor only.

The PWA is the right starting point — ship it, get feedback, then go native if it earns its keep.
