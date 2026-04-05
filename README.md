# Number Rails Racing 3D

A 3D racing game that makes learning French vocabulary, numbers, and multiplication tables genuinely fun. Built as a single HTML file with no dependencies, no build tools, and no server required.

**[Play Now](https://finnliebold.github.io/Number-Rails-Racing-3D/)**

---

## What is this?

Number Rails Racing puts you behind the wheel of a car speeding down a 3D road. To keep driving, you need to pick the correct translation or answer from three lanes. Answer wrong or run out of time, and it's game over. The faster you go, the harder it gets.

What started as a simple French number quiz evolved through many iterations into a full-featured learning game with spaced repetition, multiplayer, weather systems, and a garage full of cars.

## Features

### Learning
- **220+ vocabulary words** across 4 languages (German, French, English, Spanish)
- **8 game modes** including number translation (DE/FR), vocabulary drills, multiplication tables (easy/medium/hard), and a MIXMODE that combines everything
- **Spaced Repetition algorithm** (SM-2 based) that tracks every answer per profile. Words you get wrong appear more frequently. Words you master fade into the background. Each profile maintains independent SR data
- **Progressive difficulty curve** (optional) that starts with easy content and ramps up every 5 correct answers, with a shrinking timer

### Gameplay
- **6 biomes**: Day, Night, Desert, Snow, Space, and Royal (exclusive unlock)
- **Dynamic weather**: Rain with splash effects, thunderstorms with lightning and screen shake, fog with drifting layers
- **Timed modes**: 30 seconds, 1 minute, 2 minutes, 3 minutes, 5 minutes, or endless
- **2-Player split-screen**: Player 1 on keyboard (A/W/D), Player 2 with mouse. 6-lane road, independent questions, skin selection before the race
- **Visual feedback**: Screen flash on correct/wrong, screen shake on errors, speed lines at high velocity, streak counter

### Cars & Customization
- **39 cars** across 6 categories: Starter, Sport, Luxury, Special, Legendary, and seasonal
- **Car Garage** with side-view display and upgrade system (tires, spoiler, windows across 5 levels each)
- Cars range from the free Classic Orange to the 100,000-coin Royal car with animated gold trim
- Each car has a unique rear-view (in-game) and side-view (garage) design, all built purely with CSS

### Progression
- **Profile system** with independent save data per player
- **Badge system** with 20+ achievements tracking games played, scores, coins earned, cars owned, speed records, and drive time
- **Coin economy**: Earn coins per correct answer, with car-specific bonuses from upgrades
- **Car shop** organized by category with preview renderings

### Polish
- **Procedural music engine** generating synthwave tracks in real-time using Web Audio API, with separate menu, gameplay, and game over tracks that adapt to game speed
- **Sound effects** for correct/wrong answers with independent volume control
- **Full localization** in German, English, and Spanish, including all UI, game text, vocabulary, and mode descriptions
- **Settings panel** with music volume, SFX volume, and language selection
- **Responsive design** with controller/gamepad support

## Technical Details

The entire game is a single `index.html` file (~12,000 lines). No frameworks, no build step, no server. It runs from `file://` or any static host.

**Technologies used:**
- Vanilla HTML, CSS, and JavaScript
- CSS 3D transforms for the road perspective and car rendering
- Web Audio API for procedural music and sound effects
- localStorage for profile data, settings, and spaced repetition state
- Google Fonts (Orbitron, Inter) loaded via CDN

**Spaced Repetition implementation:**
The SR system is based on the SM-2 algorithm. Each vocabulary item, number, or multiplication problem is tracked independently per profile with the following data:

- `ease`: Factor controlling interval growth (starts at 2.5, minimum 1.3)
- `interval`: Time until next review (in minutes)
- `reps`: Consecutive correct repetitions
- `nextReview`: Timestamp for when the item is due
- `correct` / `wrong`: Lifetime counters

On a correct answer, the interval grows exponentially (1 min, 3 min, then `interval * ease`). On a wrong answer, the interval resets to 30 seconds and the ease factor decreases. When selecting questions, the algorithm prioritizes overdue items and high error-rate items 60% of the time, with 40% random selection to maintain variety.

## Development

This project was built through extensive iterative development using [Claude Code](https://claude.ai/code) in VS Code. Starting from a basic number translation quiz, each feature was added incrementally through conversation-driven development. The game grew organically from a simple learning tool into a full racing game with dozens of interlocking systems.

Key development milestones:
1. Core quiz mechanics with German-French number translation
2. 3D road perspective and car rendering with CSS
3. Biome system with themed environments
4. Car shop and skin system
5. Procedural music engine
6. Settings panel and i18n system
7. Timed modes and victory sequence
8. Multiplayer split-screen
9. Weather system
10. Profile system and spaced repetition algorithm
11. Progressive difficulty curve
12. 220+ vocabulary with 4-language support

## How to Play

**Single Player:**
- `Arrow Left` / `Arrow Up` / `Arrow Right` to pick a lane
- Answer the question by choosing the correct translation
- Earn coins and unlock cars

**2 Player:**
- Player 1: `A` / `W` / `D` keys
- Player 2: Mouse click on answers
- First wrong answer loses

## Deploy Your Own

1. Fork this repository
2. Go to Settings > Pages > Source: main branch
3. Your game is live at `https://yourusername.github.io/number-rails-racing/`

Or simply open `index.html` in any browser.

## Contact

Have cool update ideas? Open an issue on this repository.
Please stay serious.

## License

MIT License

## Author

**Finn Liebold**

---

*Built with the help of [Claude Code](https://claude.ai/code) through iterative AI-assisted development.*
