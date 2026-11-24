# Testing
*by Abdurrahman Khan*

## Flags
| URL suffix | Use |
|---|---|
| `?preview=1` | all levels/features open (normal build) |
| `?reset=1` | wipe save on this device |
| `?gate=1` | show gate riddle in preview |
| `?bd=1` | birthday theme |

`unlocked/` build already has preview on.

## Smoke test (5 min, on a real phone)
1. Gate riddle appears (during 24 Nov–17 Dec) → solve → login.
2. Login works; music starts after first tap; 🔊 button mutes.
3. Hub shows tiles, countdown, cake widget.
4. Play one level to the end; light turns on; message + reward show.
5. Lose a rigged level once → fail scene + complaint box.
6. Open Jokes, rate one (👍).
7. Lantern Night: music plays; if not, **Tap to play** appears; light 2 lanterns.
8. Leave the app 10+ s, return → one *Session summary* email arrives.
9. Airplane mode → reload → app opens (offline cache).
10. Update test: bump `sw.js`, redeploy, reopen → new version loads.

## Lantern audio checks
- File: ~108 s, MP3, no cover art, mean volume ≈ −26.6 dB.
- iPhone: silent switch should not mute it (`audioSession=playback`).
- If silent: button appears after 2.5 s; if audio errors, Web Audio fallback runs.

## Regression list
Login · saves after reload · level unlock dates · rewards granted once · email queue offline → flush online · themes toggle · feedback edition on 18 Dec · no console errors.

## Known test limits
Headless browsers cannot judge audio quality; test sound on a phone.
