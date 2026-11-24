# Maintenance
*by Abdurrahman Khan*

## Where to edit (top of `<script>` in `index.html`, block "EDIT ME")
| Want to change | Edit |
|---|---|
| Level messages + rewards | `MESSAGES` |
| Notes after win / fail | `NOTE_FROM_ME`, `NOTE_FAIL` |
| Rabbit lines | `ARZA` |
| Fortunes / wishes | `FORTUNES`, `WISHES` |
| Final letter | `FINAL_LETTER` |
| Login / hints | `USERNAME`, `PASSWORD`, `HINT_USER`, `HINT_PASS` |
| Birthday date / step | `BDAY`, `STEP_DAYS`, `TZ` |
| Email | `OWNER_EMAIL`, `WEB3FORMS_KEY` |
| Rewards table | `REW` |
| Gate riddles | `GATE` · Riddle Master: `RM` |
| What's new page | `VERSIONS` |

## Audio
Files live in `music/`. Ambience = `seaquest`, `ethereal` (quiet on purpose, ≈ −26 dB). Replacing a file: keep the name, add/bump `?v=` where it is referenced, bump `sw.js`.

## Adding a game
1. Write `run(stage, finish)`; call `finish(true)` on win.
2. Add `SUB('id','Name','🎮',level,run)` to the level's `sub` list.
3. Add a guide line in `GUIDE`.

## Routine
- Every release: bump `sw.js`, update `CHANGELOG.md` and `VERSIONS`.
- Keep repo private. Never commit other people's data.
- Watch the Web3Forms monthly quota.

## Backup
`git push` is the backup. Zhalla's progress backup = progress code in emails.
