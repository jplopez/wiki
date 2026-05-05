[[toc]]

# PacLike Game Design Document

This document consolidates the group’s brainstorming and decisions into a structured design reference for the Pac-Man-inspired game project.

## 1. Concept Overview

A modernized Pac-Man-style game with retro neon aesthetics and enhanced mechanics. The design emphasizes:

* Neon lighting and glow effects for characters and walls.
* Classic Pac-Man gameplay with modern responsiveness.
* Progressive difficulty scaling through ghost AI and level design.

## 2. Themes & Inspirations

* Retro Arcade Vibe: Neon-lit walls resembling glowing tubes.
* Modern Platformer Lighting: Halo/glow effects around Pac-Man and ghosts.
* Classic Pac-Man Familiarity: Early levels closely mimic original Pac-Man.
* Creative Expansion: Later levels introduce unique styles, decorations, and lighting variations.

## 3. Draft Ideas

### 3.1 Visual & Animation

* Pac-Man: Soft glow around character, bounce animation when hitting walls, rotation animation when turning.
* Ghosts: Cloth-like floating animation, faint colored glow/halo, tinted shadows matching ghost color.
* Walls: Neon light tubes, bloom effects, ambient lighting variations.
 
### 3.2 Player Movement

* Grid-based movement with smooth animation.
* Forgiveness mechanics:
  * ***Coyote Time***: Allow turns slightly past the tile.
  * ***Input Buffering***: Queue turns slightly before reaching the tile.
* Collision feedback: bounce + sound cue.

### 3.3 Ghost AI

* Pathfinding via A*.
* Difficulty scaling through recalculation frequency, speed, and turning rules.
* Modes: chase, scatter, flee.
 
### 3.4 Level Storage & Architecture

* Level Scriptable Object (LevelSO): Tracks progression, scene references, prefab references.
* Level Prefabs: Contain maze layout, level manager, pellet/power-up configuration, portals, difficulty parameters.
* Scenes: Define visual style (e.g., classic Pac-Man vs. neon custom).
* Persistent Systems: Player controller, HUD, score/lives manager.

## 4. Feedback & Iterations

* Early levels (1–5): Classic Pac-Man look, simple portals.
* Later levels: Custom neon styles, varied borders, lighting intensity changes.
* Flexibility to reuse scenes across multiple levels for consistent style.

## 5. Difficulty Strategy

Difficulty increases through:

1. Ghost pathfinding frequency.
2. Ghost speed.
3. Turning flexibility (intersection-only → mid-path allowed).
4. Reduced forgiveness windows for player input.
5. Maze complexity (more portals, tighter corridors).
6. Optional lighting intensity changes.

## 6. Open Questions

* Should difficulty scaling be strictly linear or include spikes for variety?
* How many total levels should be included for the game jam version?
* Should lighting intensity affect gameplay difficulty or remain purely aesthetic?

## 7. Action Items

* Define LevelSO data schema (fields for scene, prefab, progression).
* Create initial prefab for Level 1 with classic Pac-Man layout.
* Implement ghost pathfinding with adjustable recalculation frequency.
* Prototype glow/halo effects for characters and neon walls.
* Establish difficulty curve for first 10 levels.

## 8. Future Considerations

* Introduce other mechanics.
  * Moving platforms or on/off platforms.
  * Objects on walkable paths that trigger events when passing by
    * Open door
    * change path direction
  * Air puffs that can push player and ghosts into a certain direction 
