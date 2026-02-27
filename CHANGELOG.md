# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [v1.0.2] - 2026-02-27

### Added
- Added console-only runSmoke() regression harness to validate save/load, learnRule, and hold-state invariants.
- No gameplay behavior changes.

## [v1.0.1] - 2026-02-27

### Added
- Clarified CUT hints: Replay continues the loop; Save and stop ends the session.
- Clarified HOLD (4.9) behavior in-game.
- Added console-only helper forceHoldTest(cutKey) for faster testing.

## [v1.0.0] - 2026-02-27

### Added
- Beat-driven interactive fiction prototype
- Intra-beat steps system
- Loop mechanic with memory (Amanda remembers, others reset)
- CUT fail states teach rules R0,R1,R2,R3,R5,R6,R7
- Hold beat prevents repeated identical CUT loops
- Save/Load with versioning
- Rule progress indicator
- Clues panel shows rulebook entries

## [1.0.0] - 2026-02-24

### Added
- Initial release of "Fixing Up a House" interactive fiction game (Beat 1 Prototype)
- Beat-driven story progression with choices
- State tracking: Trust, Normalcy, Unease, Time
- Inventory system with pills display
- Clue logging with journal cards
- Actor notes toggle
- Typewriter effect toggle
- Save/Load functionality via localStorage
- UI with beat navigator, choice buttons, and side panels
- Responsive design with CSS variables
- Validation for beat keys and choices

### Technical
- Single-page HTML application
- Embedded JavaScript for game logic
- No external dependencies
- Runs locally in browser without server