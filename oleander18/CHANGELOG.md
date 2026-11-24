# Changelog — Zhalla's Little Universe
*by Abdurrahman Khan · format: newest first*

## v37 — 24 Nov 2026 · Smaller package
- All six mp3 files re-encoded to 64 kbps stereo (music folder 17.8 MB → about 9 MB). Faster loading on phones; volumes unchanged.
- Lantern cache-bust `?v=4`. Service-worker cache `zhalla-v37`.

## v36 — 24 Nov 2026 · Quieter lantern
- Lantern track lowered by 7 dB to match the ambience tracks (mean ≈ −26.6 dB), with 3 s fade-in and 5 s fade-out.
- Lantern URL cache-bust `?v=3`. Service-worker cache `zhalla-v36`.

## v35 — 24 Nov 2026 · Tap-to-play + session summary
- **Tap to play** button on Lantern Night if the phone blocks or silently ignores audio (checked after 2.5 s).
- **Silent session summary** email when she leaves, locks the phone or switches app (≥ 8 s sessions, max one per 20 s). Includes time stayed, screen left on, screens opened, Arza taps, jokes, lanterns, levels lit. Queued offline and sent late if needed.
- Cache `zhalla-v35`.

## v34 — 24 Nov 2026 · Lantern fix + unlocked build
- **Fix:** `lantern.mp3` would not play. Cause: 320 kbps file with an embedded 640×480 cover image and foreign container tags. Re-encoded to a clean 160 kbps MP3, no art/tags.
- Cache-bust `?v=2`; Web Audio fallback if the `<audio>` element errors.
- New **unlocked** build for testing (`PREVIEW=true`). Cache `zhalla-v34`.

## v33 — 24 Nov 2026
- 17 games per level, harder as you progress; 13 new games (Aura Math, Tea Rush, Sour Fruit Stack, Mountain Memory, Dad's Morning Check, Name That Movie, Voices, and spooky ones: Knock on the Roof, Ghost Story, Haunted Words, Find the Ghosts, Rat Facts, Ghost Math).
- Hints in 3–4 steps; Skip game / Skip level after finishing a level.
- Joke Jar ratings (👍 👎 ⭐) saved and included in feedback.
- Feedback mode: rate each level message and card.
- **Lantern Night**, the last bonus level, with music.
- Jeff Buckley and Nusrat Fateh Ali Khan cards; musician title.
- Birthday Queen theme + story *The Making of this Universe* (after feedback).
- More talkative rabbit; fixed unwinnable games (Odd One Out, Number Memory, Spot the Change).

## v32
- Arza's Cards got personal notes; wishlist ideas expanded; spelling fix "Kurdparwar".

## v28 – v31
- Daily gate riddle before login (24 Nov → 17 Dec) and the Riddle Master.
- Round two: feedback edition, unlocked 18 Dec, Newroz-themed intro.
- Joke Jar grew to ~120 jokes; Arza's Cards unlock 18 Dec.
- Cake countdown, candle and sun widgets on the main page.

## v23 (inside v1–27)
- Odd-one-out, number memory and three "rigged" prank games.

## v1 – v27
- Eight levels + birthday level, each with a light, message and reward.
- Arcade, Explore, Where It Began, Kurdistan theme, birthday pink theme.
- Music cards, titles, the witch, stories everywhere.

> Note: the in-app *What's new* page lists up to v33. v34–v37 are build-level changes and are documented here only.

*Tawakkul + Tadbeer.*
