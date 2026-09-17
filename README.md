# Spellfall

A word game that installs to your home screen and plays offline.

**Play: https://afsarsaman.github.io/spellfall/**

Letters rain into a 6×7 well. Tap letters that touch — sideways, up, down or
diagonally — one by one, or drag across them, to spell a word. It scores and clears, everything above
collapses, and the rain keeps coming. Each word counts once. Fill the well and
it's over.

## Scoring

Letter values are Scrabble-style and shown on each tile, with the tile colour
signalling rarity. Word score is the sum of its letters times a length
multiplier — 3 letters ×1, 4 ×2, 5 ×3, 6 ×5, 7 ×8 — then ×10, and multiplied
again by your streak (up to ×3, reset by a wrong guess).

## Power-ups

Start with one of each; earn more with every 5-letter word and every 4th word.

- **Blast** — clears a 3×3 block of letters you can't use.
- **Freeze** — stops the rain for 12 seconds.
- **Reveal** — searches the board for the best word you haven't played yet and
  selects it for you.

## Dictionary

16,123 words, all recognisable. Built from a subtitle frequency list
intersected with an English word list, then filtered twice: against a Scrabble
tournament dictionary to drop proper nouns, and against WordNet's
capitalisation so names like *Paris* and *Kate* are excluded while ordinary
words that double as names — *rose*, *hope*, *robin* — are kept. Inflections
(`cats`, `walked`, `biggest`) are resolved so they still count. Slurs and crude
terms are removed.

## Files

Everything is static — no build step, no dependencies.

| File | Purpose |
| --- | --- |
| `index.html` | The whole game: markup, styles, logic and the dictionary, inline. |
| `manifest.webmanifest` | Install metadata — standalone display, portrait, icons. |
| `sw.js` | Service worker. Precaches the app shell so it runs with no network. |
| `icon-*.png` | Launcher icons, including a maskable one for Android. |

**After changing anything here, bump `VERSION` in `sw.js`** — browsers keep the
old cache until that string changes.

## Publishing

GitHub Pages serves this repo's `main` branch from the root, so any push to
`main` republishes the game. `.nojekyll` keeps GitHub from running the files
through Jekyll.

## Installing

- **Android / Chrome** — an install bar appears at the bottom of the page.
- **iPhone / Safari** — tap Share, then Add to Home Screen.
