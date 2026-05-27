# Brief: host the Self-Coached OS as a PWA

Hi — I need you to host this folder on the web so I can install it on my phone. It's a Progressive Web App, so once it's online I can add it to my home screen and it runs like a native app.

## What's in this folder

7 files, all need to stay together in the same root directory:

- `self-coached-os.html` — the app
- `manifest.json` — PWA manifest (name, icons, theme)
- `sw.js` — service worker (offline cache)
- `icon-192.png` / `icon-512.png` / `icon-maskable-512.png` — app icons
- `HOST-PWA.md` — full hosting docs (read this if you get stuck)
- `BRIEF-FOR-ASSISTANT.md` — this file

Total size: ~210 KB. No build step, no dependencies, no server-side code. Pure static files.

## Hosting requirement

The service worker only works over HTTPS (or localhost). Loading directly from a `file://` path won't enable installation or offline. So it needs to be on a real URL.

## Recommended path (fastest, free, no account needed)

1. Go to **https://app.netlify.com/drop**
2. Drag this entire folder onto the page.
3. Netlify will give you a public URL like `https://random-words-1234.netlify.app`. Send me that URL.

That's it. Takes 60 seconds.

## Alternative — give me a permanent URL

If you want to rename the URL to something cleaner (e.g. `selfcoachedos.netlify.app`) or set up updates more easily:

1. Sign up for a free Netlify account (use my email if I've given it to you, otherwise yours).
2. After dragging the folder, click "Claim this site" → connect to the account.
3. Site settings → Change site name → pick something memorable.
4. Send me the final URL.

Other equally-fine free hosts: Vercel (`vercel` CLI), Cloudflare Pages, GitHub Pages. Any of them work as long as all 7 files are in the same folder at the deployed root.

## After it's hosted

Open the URL on my phone (in Safari on iPhone or Chrome on Android). The page should load. Then:

- **Android**: tap the "Install app" button in the header, or wait for the "Install" prompt at the bottom.
- **iPhone**: tap the share icon at the bottom of Safari → "Add to Home Screen".

The icon will appear on the home screen and the app will run fullscreen, offline.

## How to verify it worked before sending me the URL

1. Open the URL in any browser.
2. The splash screen with the "SC" logo should appear for ~1.5 seconds.
3. Then either onboarding (first visit) or the dashboard.
4. In Chrome devtools → Application tab → Manifest, you should see the manifest loaded with no errors.
5. Application → Service Workers should show `sw.js` registered.

If steps 4 or 5 are red, double-check that all 7 files are in the deployed root, not in a subfolder.

## How to push updates later

When I send you a new version of `self-coached-os.html`:
- Replace just that file in the host (Netlify lets you re-drag).
- Open `sw.js` and bump the line `const CACHE = 'sc-os-v2'` to `v3` (or whatever's next). This forces the new version to replace the cached one on every device.

That's everything. Thanks!
