# Year 6 Arcade

A fresh arcade for Year 6, built on the same setup as the Year 5 one.

## What's here

- `index.html` — the launcher: sign-in, avatars, term filter, My Records.
- `word-cross.html` — Word Cross (`y6-wordcross`): a crossword built from twelve weekly words, with the meanings as the clues. Gentle and Normal show a word bank beside the grid to copy the spelling from; Challenge hides it and pays double points. It keeps its OWN `WEEKS` list — Word Hunt has a separate list, so **both must be updated each week**.
- `word-hunt.html` — Word Hunt (`y6-wordhunt`): a weekly word search. Each week's words go in the `WEEKS` list at the top of its script (any number — Week 1 has twelve); the game auto-picks the newest list whose Monday has passed, and its leaderboard has an all-time top 15 and a this-week top 15.
- `teacher.html` — the teacher dashboard.

## What carries over, what doesn't

| | |
|---|---|
| Login name + password + avatar | **Carries over** — same shared `players` table, same `rna_player` key in localStorage. She signs in exactly as before. |
| Scores and leaderboards | **Fresh start** — Year 6 only ever shows games whose `GAME_ID` starts with `y6-`. Year 5 scores stay in the Year 5 arcade. |

## Adding a game

1. Build the game `.html` and drop it in this folder.
2. Give it a `GAME_ID` starting with `y6-` (e.g. `y6-fraction-frenzy`). Never reuse an id.
   Everything else in the shared backend block stays identical — same Supabase project and key.
3. In `index.html`:
   - Add the `<a class="card …">` block inside the right term's `<div class="cards">`, and delete
     that term's `<div class="soon">` placeholder.
   - Bump the term's `<div class="term-count">`, its pill `<span class="pn">`, and the `✦ All 0` pill.
   - Add a theme CSS block for the new card class (plenty of ready-made ones are already in the
     `<style>` block — `.siege`, `.nebula`, `.jungle`, etc.).
   - Add a friendly name to `Y6_GAMES`, e.g. `'y6-fraction-frenzy':'🍕 FRACTION FRENZY',`.
     (Skip it and the record still works, just with an auto-generated name.)
   - Nothing to do for the sign-in lock — `setCardsLocked()` now locks every card automatically.
4. In `teacher.html`: add the same id to `GAMES` for a friendly name in the filter and reports.
   (Again optional — any `y6-` game is counted either way.)

## Terms

The sections are `weekly` (Word of the Week — not a school term, it holds Word Hunt and Word Cross), `autumn`, `spring`, `summer1`, `summer2`. (There was a `books` section for class reads; it was removed.) The headings say
"Topic to be added" — swap in the real Year 6 topics when they're known.
