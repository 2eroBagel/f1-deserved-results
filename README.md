# F1 Deserved-Results Engine

**[Live dashboard →](https://2erobagel.github.io/f1-deserved-results/)**

A from-scratch model that splits every 2022–2025 Formula 1 result into three parts: the pace a driver showed, how they drove on the day, and the luck that moved them. Strip the luck out and you can rate drivers on what they actually earned.

## What it does

- **Luck decomposition.** Every race result gets broken into expected pace, race-day drive, and luck. Luck is measured in positions and split into four buckets: retirements ahead, safety-car timing, pit-crew time, and forced strategy.
- **Luck-removed standings.** Re-scores every race and sprint with the luck taken out, then rolls it into a championship table. The 2025 title flips once luck is removed.
- **Performance rating.** A chess-style Elo built on luck-removed finishing order. Crashes a driver caused count against them; mechanical failures and getting taken out don't move the rating.
- **Race-by-race.** Pick any race and see the full field sorted by how it should have gone with the luck removed, DNFs classified by cause.

## How it's built

- **Pace baseline:** teammate-relative race pace, fit per season with cross-validated hyperparameters.
- **Data:** FastF1 for lap timing, pit stops, and stewards messages; F1DB for sprint results and points. ~100k race laps, 240+ classified DNFs, all pulled and cleaned from scratch.
- **Stack:** Python (pandas, numpy), self-contained HTML/JS dashboard with the data baked in.

## Known limits

- The rating runs on finishing position, which still carries some car performance, it's a luck-removed results rating, not a pure isolated-driver-skill number. A fully car-controlled version is the planned next build.
- Strategy and safety-car luck are the most approximate of the four buckets and are scaled down accordingly.
- Covers the ground-effect era, 2022 to 2025. Extending back to 2018 is in progress.

Built by James Nagel.
