# SE LAB 04: Endless Runner Game, LLM-assisted Bug Fixing & Enhancement

## PROBLEM STATEMENT

Use an LLM assistant to identify, debug, refactor, and expand features in a Python/Pygame-based **Endless Runner** game. The project requires diagnosing game loop bugs, managing dynamic obstacle generation and player collision physics, implementing score/health state trackers, and documenting the iterative debugging session via a shared LLM chat link and before/after gameplay recordings.

---

## Project Specifications & Architecture (`Endless-runner-game`)

* **Technology Stack:** Python 3.12, Pygame 2.6.1 (`requirements.txt`)


* **Core Module Structure:**
* `main.py`: Entry point controlling the overall application lifecycle, frame rate, and primary game loop states (Start, Playing, Game Over).
* `game_engine.py`: Manages game updates, collision detections, speed scaling over time, and event routing.
* `player.py`: Handles player character movement mechanics, jump/gravity physics, boundaries, and rendering states.
* `obstacle.py`: Handles procedural generation of obstacles, positioning, movement speeds, and bounding-box hitboxes.


* **Key Enhancements / Fixes Addressed via LLM:**
* Resolving collision boundary bugs and hitbox overlaps between the player and incoming obstacles.
* Optimizing frame rate stability and smooth rendering during accelerated scrolling loops.
* Implementing game-over condition triggers, lives/health management, and score tracking metrics.
