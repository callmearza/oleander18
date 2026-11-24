# Deployment
*by Abdurrahman Khan*

## Requirements
GitHub account (`callmearza`), Vercel account (free), Web3Forms key (already in `index.html`).

## A. First deploy from GitHub
1. Create a **private** repo, e.g. `zhallas-little-universe`.
   ```bash
   git remote add origin https://github.com/callmearza/zhallas-little-universe.git
   git push -u origin main
   ```
2. Vercel → **Add New → Project → Import** the repo.
3. **Root Directory: `normal`** · Framework: *Other* · Build command: *(empty)* · Output: *(empty)*.
4. Deploy. Open the URL on a phone and test (see TESTING.md).

## B. Drag-and-drop alternative
Drag the **`normal/`** folder onto vercel.com/new. Or `cd normal && vercel --prod`.

## C. Headers (`vercel.json`)
| Path | Cache-Control |
|---|---|
| `/sw.js`, `/index.html` | `no-cache` (always revalidate) |
| `/music/*` | `public, max-age=86400` |

Because music is cached for a day under the same filename, **change the query string** (e.g. `?v=4`) or the filename whenever you replace an mp3.

## D. Release checklist
1. Edit files in `normal/` (and mirror in `unlocked/`, or regenerate it).
2. Bump `const C='zhalla-vNN'` in `sw.js`.
3. Update `CHANGELOG.md`.
4. Test with `?preview=1` on a phone.
5. `git commit` → `git push` → Vercel auto-deploys.
6. Check one real device: login, a level, Lantern Night music.

## E. Changing the URL / host
Browser storage is **per origin**. A new URL means Zhalla starts at 0 and must re-add the home-screen icon.
- Decide the final URL **before** she is deep in the game.
- If you must move: keep the old site live, add a "we moved" notice, and give her the new link. Her progress code (e.g. `110000000`) is in your emails if you need to restore it by hand.
- Custom domain: Vercel → Project → Settings → Domains.

## F. Rollback
Vercel → Deployments → pick the last good one → **Promote to Production**. Then bump the cache name again so phones refetch.

## G. Email reports
Free Web3Forms plan has a monthly cap. Reports are queued on her phone if sending fails.
