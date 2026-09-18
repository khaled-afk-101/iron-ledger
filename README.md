# Iron Ledger — install it as an app

A workout log that runs as a real app on a phone: its own icon on the home screen,
opens fullscreen with no browser bars, works with no signal in the basement of a gym,
and needs no account of any kind.

It's a website that behaves like an app (a "PWA"). That's what lets it skip the App Store.

## What's in this folder

| File | What it is |
|---|---|
| `index.html` | The whole app — all the code, in one file |
| `manifest.webmanifest` | Tells the phone the app's name, icon and that it opens fullscreen |
| `sw.js` | The offline cache. This is what makes it work without signal |
| `icon-*.png` | Home screen icons |

All four need to sit **in the same folder** on the web. Don't rename them.

---

## Step 1 — Put the folder on the web

It needs an `https://` address. Three free ways, easiest first.

### Option A — Netlify Drop (about two minutes)

1. Go to **app.netlify.com/drop**
2. Drag this whole `iron-ledger` folder onto the page
3. You get a live link immediately — no account needed to deploy

One catch: an unclaimed site is password-protected until you claim it. Make a free Netlify
account and click "claim" so the link works normally and stays up. Free tier is far more
than this app will ever need.

### Option B — GitHub Pages (free forever, a bit more fiddly)

1. Make a free GitHub account
2. New repository → name it `iron-ledger` → Public
3. "Add file" → "Upload files" → drag all the files in → Commit
4. Settings → Pages → Source: "Deploy from a branch" → Branch: `main`, folder `/ (root)` → Save
5. After a minute the link appears at the top of that Pages settings screen

### Option C — Cloudflare Pages or Vercel

Same idea as Netlify: free account, upload the folder, get a link. Pick whichever you
already have an account for.

---

## Step 2 — Put it on the home screen

### iPhone / iPad

1. Open the link **in Safari** (this doesn't work from Chrome on iOS)
2. Tap the Share button — the square with the arrow
3. Scroll down, tap **Add to Home Screen**
4. Tap Add

The icon appears with the other apps. Opening it gives a fullscreen app with no address bar.

### Android

Open the link in Chrome. It usually offers **Install app** by itself — if not, use the
three-dot menu → **Add to Home screen**.

---

## About your data

Workouts are stored **on that phone**, in that app. Nothing is uploaded anywhere, no
account exists, and nobody else can see it. The flip side: it does not sync between
devices, and it is not backed up by anything.

So: **Progress tab → Export backup** now and then. It saves a small `.json` file you can
keep in Files, iCloud Drive or email to yourself. On a new phone, install the app and use
**Restore backup** to load it back in.

Worth doing this every month or so, and definitely before changing phones or clearing
Safari's website data — on iOS, storage for a site can be cleared if the app goes unused
for a long stretch.

---

## Trying it without hosting it

Double-clicking `index.html` opens it in a browser and the app works, but you won't get
the home screen icon or reliable offline storage — browsers restrict files opened this way.
Fine for a look, not for real use.

---

## What about a proper App Store app?

Possible, not worth it here. It would need:

- A Mac with Xcode
- An Apple Developer account — **$99 per year**
- Wrapping this same page in a native shell (Capacitor, or PWABuilder, which can generate
  store-ready packages from exactly this kind of app)
- Apple's review process, and a re-review for every update

You'd get the same app, minus the ability to fix a typo in thirty seconds. The home screen
install above is indistinguishable in daily use — the only real differences are that a
PWA can't send push notifications on iOS as freely, and it won't appear in App Store search.

If she ever wants it on Google Play, that path is much cheaper: a one-off $25 and
PWABuilder can package it more or less as-is.
