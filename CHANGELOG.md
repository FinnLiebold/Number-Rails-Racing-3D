# Changelog

All notable changes to Number Rails Racing 3D are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased] - 2026-05-05

### Added
- **Gift code redemption** - pink/magenta 🎁 button in the start-menu top right opens a modal where players can redeem one-time codes worth 5,000 coins each. Codes are stored as SHA-256 hashes; redemptions are tracked per profile so a code can only be used once.
- **Mystery Box** - purple `❓ Mystery Box` button on the start menu. Costs 200 coins per roll: 80% small (+100), 19% medium (+800), 1% legendary (random Legendary skin; if you already own it, you receive coins equal to the car's price). Animated lid-pop reveal with rarity-tinted result tag. Open count is persisted per profile.
- **First-run tutorial tour** - five-step tooltip walkthrough that highlights the mode selector, start button, Car Garage, Mystery Box, and stats box. Triggers automatically on profile selection (only when `tutorialDone` is false), uses an inverse box-shadow spotlight effect, and is replayable from Settings → Tutorial → Replay Tutorial.
- **In-run power-ups** - bar at the bottom of the gameplay screen with three power-ups: ⏭️ Skip (re-rolls the current question), ⏰ Slow Time (halves speed for 5 s and pauses speed acceleration), 💎 Coin Boost (next correct answer pays +2 coins on top of normal payout). One charge of a random type is awarded each time the streak hits a multiple of 10. Activate by clicking or with keys 1 / 2 / 3. Charges reset between games.

### Changed
- **Car catalogue repriced** - Luxury (excluding Royal) and Legendary tiers now scale 1,000–5,000 coins (was 150–500). Royal remains at 100,000.
- **Mystery Box duplicate handling** - when a Legendary roll lands on a car you already own, you now receive coins equal to that car's price instead of the previous flat 5,000-coin fallback. The fallback constant has been removed.
- **Power-up bar layout** - compact 38 × 38 buttons at the very bottom of the screen so the lane answers and the player car stay clear.

### Fixed
- **Gift button visibility** - the 🎁 button was being occluded by the ADMIN button at the top right; shifted further left so both icons are now visible side by side.

## [2026-05-04]

### Added
- **Statistics box on start menu** - a dark panel below the Car Garage button shows five horizontal bar metrics: Games, High Score, Correct, Mistakes, and Accuracy %. Refreshes after every game and on language switch.
- **Mistake tracking** - new `totalWrong` stat persisted in the player profile. Incremented on each wrong answer and used by the accuracy calculation.
- **i18n keys for the stats box** - `statsTitle`, `statGames`, `statHighScore`, `statCorrect`, `statMistakes`, `statAccuracy` added for English, German, and Spanish.
- **Admin Panel - Run Events tab** - second tab next to "Grant Coins" hosting four one-hour buffs:
  - **2× Coins** - doubles coin gain per correct answer.
  - **2× Score** - doubles score gain (faster badge progression).
  - **Forgiveness** - wrong answers no longer end the game.
  - **Slow Mode** - pauses speed acceleration at the current speed.

  Each event card shows a live HH:MM:SS countdown; the button toggles between **START 1H** and **STOP**. Event state is persisted per profile and survives reloads.

### Changed
- Admin access code rotated. The new code's SHA-256 hash replaces the previous constant in `index.html`.
