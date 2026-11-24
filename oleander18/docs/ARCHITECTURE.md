# Architecture
*Zhalla's Little Universe · by Abdurrahman Khan*

## 1. Shape of the system

```
 Phone browser / installed PWA
 ┌──────────────────────────────────────────────┐
 │ index.html  (HTML + CSS + ~2,400 lines JS)    │
 │  ├─ EDIT-ME block  (text, dates, credentials) │
 │  ├─ State  ST  ──► localStorage + cookie      │
 │  ├─ Router nav()/draw()/V.*  (24 views)       │
 │  ├─ Engines: time-unlock, audio, FX, reports  │
 │  └─ Content: levels, games, jokes, cards      │
 │ sw.js  ──► cache + offline                    │
 └───────────────┬──────────────────────────────┘
                 │ HTTPS (static)         │ POST (JSON)
            Vercel CDN              api.web3forms.com ──► Abdurrahman's inbox
```
No server code, no database, no build tool. Everything is static files.

## 2. Boot sequence (`index.html`, bottom of file)
1. `loadState()` reads `zhalla_v3` from `localStorage` (falls back to cookie `zp`).
2. `persist()` writes state back.
3. `ST.auth=false` (she must log in every visit).
4. First view = `gate` (daily riddle, 24 Nov → 17 Dec, once per Hawler day) else `login`.
5. `draw()` renders; `flushQ()` retries any queued emails.

## 3. State (`ST`)
One JSON object; saved after every meaningful action. Key fields:

| Field | Meaning |
|---|---|
| `auth` | logged in this visit (never persisted as true across loads) |
| `done[9]` | level lights (true/false) |
| `failed{}` | levels whose rigged first try was lost |
| `sub{}` | per-level game progress |
| `rw{}` / `title` | rewards earned / equipped title |
| `ex{}` / `exd` | Explore tasks / all-done flag |
| `kt`, `bq`, `bt` | Kurdistan theme, Birthday Queen theme, birthday theme toggle |
| `jr{}` | joke ratings (👍👎⭐) |
| `ln{n,done}` | lanterns lit / finale done |
| `fb{on,sent}` | feedback edition state |
| `gd`, `rm` | last gate day solved, Riddle Master progress |
| `wish{}` | wishlist (movies, trips, 1/5/10-year) |
| `q[]` | outbound email queue (offline safe) |
| `dev`, `visits`, `taps`, `laughs`, `nope`, `mute` | device id and counters |

## 4. Router
`nav(name,args,replace)` → sets `view`, pushes `history`, calls `draw()`.
`draw()` clears timers, records the view for the session summary, then calls `V[view.n](args)`.

Views (`V.*`): `gate login tour celebrate hub level explore cards jokes lantern notes makers arcade ag wish msg treasure begin again feedback rmaster scard acards fortune`.

## 5. Time engine
```
BDAY       = 2026-12-17 00:00 +03:00
STEP_DAYS  = 3
GAME_START = BDAY − 8×3 days = 23 Nov 2026
gT(i)      = GAME_START + i×3 days       (level i opens)
gOpen(i)   = PREVIEW || feedback-round || now ≥ gT(i)
FB_AT = ACARD_AT = BDAY + 1 day          (18 Dec)
```
| Level | Opens (Hawler 12 AM) |
|---|---|
| 1 | 23 Nov |
| 2 | 26 Nov |
| 3 | 29 Nov |
| 4 | 2 Dec |
| 5 | 5 Dec |
| 6 | 8 Dec |
| 7 | 11 Dec |
| 8 | 14 Dec |
| 9 (Birthday) | 17 Dec |

## 6. Levels and games
`LEVELS[]` holds 9 level objects. Each level has a list of mini-games built by `SUB(id,name,emoji,level,run,extra)`. Games are functions `run(stage, finish)`. Level 3 and others have a deliberately **rigged first attempt** (`failScene`) with a note from Abdurrahman, then a fair retry.

## 7. Audio
- **Ambience** `Snd`: `seaquest.mp3` → `ethereal.mp3` loop, starts on first tap (browser autoplay rule). Modes: `amb`, `card`, `bday`.
- **Cards** play reward tracks (`playCard`).
- **Lantern Night** uses its own `Audio` element (`music/lantern.mp3?v=4`), 108 s, with timed cues; Web Audio fallback; **Tap to play** button if blocked.
- Synth sounds (`pluck`, `boxTone`, `jingle`) use WebAudio, no files.

## 8. Reporting (Web3Forms)
`send()` POSTs JSON. On failure `queue()` stores it; `flushQ()` retries at next login. Every email appends a **device report** (device id, lights, progress string, time, user agent).
Session summary: `ssSend()` on `visibilitychange(hidden)` and `pagehide`, using `fetch(...,{keepalive:true})`.

## 9. PWA / service worker
- Network-first for same-origin GET; cache fallback offline; mp3 and Range requests bypass the worker.
- Cache name `C` must change every release.

## 10. Design rules (content)
Platonic, friendly, cheerful tone; no romantic emojis. Name shown in Sorani (ژاڵە). Footer credit on every screen. Hints never spoil; fail scenes roast gently.
