# Changelog

All notable changes to Number Rails Racing 3D are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased] — 2026-05-04

### Added
- **Statistics box on start menu** — a dark panel below the Car Garage button shows five horizontal bar metrics: Games, High Score, Correct, Mistakes, and Accuracy %. Refreshes after every game and on language switch.
- **Mistake tracking** — new `totalWrong` stat persisted in the player profile. Incremented on each wrong answer and used by the accuracy calculation.
- **i18n keys for the stats box** — `statsTitle`, `statGames`, `statHighScore`, `statCorrect`, `statMistakes`, `statAccuracy` added for English, German, and Spanish.
- **Admin Panel — Run Events tab** — second tab next to "Grant Coins" hosting four one-hour buffs:
  - **2× Coins** — doubles coin gain per correct answer.
  - **2× Score** — doubles score gain (faster badge progression).
  - **Forgiveness** — wrong answers no longer end the game.
  - **Slow Mode** — pauses speed acceleration at the current speed.

  Each event card shows a live HH:MM:SS countdown; the button toggles between **START 1H** and **STOP**. Event state is persisted per profile and survives reloads.

### Changed
- Admin access code rotated. The new code's SHA-256 hash replaces the previous constant in `index.html`.
