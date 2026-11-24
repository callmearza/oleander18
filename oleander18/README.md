# 🌸 Zhalla's Little Universe

> A birthday web-game for Zhalla's 18th (17 Dec 2026). Designed and engineered by **Abdurrahman Khan** (GitHub: [@callmearza](https://github.com/callmearza)).
> *Tawakkul + Tadbeer — Trust Allah, Then Do the Work.*

A single-page, offline-capable web app (PWA): 9 levels that unlock every 3 days, 17 games per level, an arcade, a joke jar, reward cards, music, a daily gate riddle, a lantern-night finale, and a rabbit guide named **Arza**. No build step, no framework, no backend.

---

## Quick facts

| | |
|---|---|
| Stack | Plain HTML + CSS + JS in one `index.html` |
| Hosting | Vercel (free), static |
| Email reports | Web3Forms (free key) |
| Saves | Browser `localStorage` + cookie backup (per device, per URL) |
| Offline | Service worker (`sw.js`), installable PWA |
| Time zone | Unlocks at 12:00 AM **Hawler (UTC+3)** |
| Current build | **v37** (service-worker cache `zhalla-v37`) |

## Repository layout

```
zhallas-little-universe/
├── README.md            ← you are here
├── CHANGELOG.md         ← version history
├── .gitignore
├── normal/              ← ✅ SHIP THIS (levels unlock by date)
│   ├── index.html       ← the whole app
│   ├── sw.js            ← service worker (bump cache name every release)
│   ├── manifest.webmanifest
│   ├── vercel.json      ← cache headers
│   ├── icon-180/192/512.png
│   └── music/           ← 6 mp3 files
├── unlocked/            ← 🧪 TEST ONLY (every level open)
└── docs/
    ├── ARCHITECTURE.md
    ├── DEPLOYMENT.md
    ├── TESTING.md
    ├── MAINTENANCE.md
    └── Zhalla_Little_Universe_Engineering_File.docx   ← full engineering file
```

`normal/` and `unlocked/` are **identical except one line**: `const PREVIEW=...` in `index.html`.

## ⚠️ Keep this repo PRIVATE

`index.html` contains the login/password gate text and the Web3Forms key. The gate is a friendly puzzle, not security, but a public repo would spoil it and expose your email key. **GitHub → Settings → Danger Zone → Change visibility → Private.**

## Deploy in 2 minutes (Vercel)

1. Push this repo to GitHub (private).
2. Vercel → **Add New → Project** → import the repo.
3. **Root Directory = `normal`**. Framework = *Other*. No build command.
4. Deploy. Done. Details: [docs/DEPLOYMENT.md](docs/DEPLOYMENT.md).

Every release: bump `const C='zhalla-vNN'` in `normal/sw.js` so phones fetch the update.

## Test links (add to the URL)

| Link | Effect |
|---|---|
| `?preview=1` | Unlock every level and feature |
| `?reset=1` | Wipe saved progress on **this** device |
| `?gate=1` | Force the daily gate riddle even in preview |
| `?bd=1` | Force birthday theme |

> Never send `?reset=1` to Zhalla.

## What it does

- **9 levels** (8 + birthday), each with a light ✨, a message and a reward.
- **17 games per level**, harder as you go; staged hints; skip after finishing.
- **Arcade** (8 games), **Joke Jar** (~120 jokes with 👍👎⭐), **Wishlist**, **Fortune**, **Treasure**, **Explore** (12 tasks).
- **Daily gate riddle** 24 Nov → 17 Dec, plus **Riddle Master** (25 riddles).
- **Music cards** (5 tracks) + **Lantern Night** (last bonus level, quiet ambient track).
- **Feedback edition** and **Arza's Cards** unlock 18 Dec; **Birthday Queen** theme + *The Making of this Universe* after feedback.
- **Silent reports** to Abdurrahman: login, level win/fail, messages, complaints, lanterns, and a **session summary** when she leaves.

## Documentation

| File | Read it for |
|---|---|
| [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) | How the code is organised and how it runs |
| [docs/DEPLOYMENT.md](docs/DEPLOYMENT.md) | Vercel, caching, release steps, moving hosts |
| [docs/TESTING.md](docs/TESTING.md) | Test flags, checklist, lantern audio test |
| [docs/MAINTENANCE.md](docs/MAINTENANCE.md) | Where to edit text, music, dates |
| [CHANGELOG.md](CHANGELOG.md) | Every version |
| `docs/…Engineering_File.docx` | Complete professional engineering document |

## 🧠 YAAD RAKHEIN

1. Ship **`normal/`**, test with **`unlocked/`**.
2. Har release pe **`sw.js` ka version badhao**.
3. Repo **private** rakho.
4. URL badla = progress reset (har URL ka apna save).

---
Made with joy by **Abdurrahman Khan** · *With joy, for your joy.*
