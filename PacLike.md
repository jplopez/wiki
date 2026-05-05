[[toc]]

# Game Idea


This project is a gamejam Pacman-like submission (`PacLike`) focused on: faithful recreation, a strong twist, and overall game feel.


# Game Design & Development Summary

This document consolidates the latest decisions on **player movement**, **ghost AI**, **difficulty progression**, **animation rules**, and **level storage architecture** for your Pac‑Man–inspired game.


## Portal Mechanics Twist


**Baseline reference** 
original Pac-Man side portals connect left and right map edges at fixed horizontal positions.

**PacLike twist**
- Portals become color-coded links (neutral light by default, distinct colors in later levels to signal valid pairs).
- Portal placement is broader than OG Pac-Man: both edge and mid-stage portal placements are expected to create tunnel-like routing.
- Levels may contain multiple disconnected maze sections/rooms that are traversable only through portal links.
- Core level-design goal: layouts are no longer a single maze; use layered, room-like structures connected by intentional portal paths.

## 1. Player Movement System

### 1.1 Core Movement Rules
- Movement is **grid‑based**, even though the on‑screen motion is smooth.
- Pac‑Man continues moving in the **last valid direction** until:
  - The player inputs a new direction **and** the turn is possible.
  - He hits a wall (movement stops, but animation continues).

### 1.2 Forgiveness Mechanics
To avoid stiffness and improve responsiveness:

- **Coyote Time (Post‑Turn Forgiveness)**  
  If Pac‑Man moves *slightly past* the turning tile, the game still allows the turn.

- **Input Buffering (Pre‑Turn Forgiveness)**  
  If the player presses a direction *slightly before* reaching the turn tile, the turn is queued and executed at the correct moment.

### 1.3 Movement Parameters
Each level can tune:
- `speed`
- `coyoteTimeWindow`
- `inputBufferWindow`

These parameters allow fine‑tuning difficulty and feel.

### 1.4 Wall Collision Feedback

When Pac‑Man hits a wall:

- A small **bounce animation** plays.
- A **sound cue** triggers.
- Pac‑Man’s chomp animation continues, but movement is halted.

### 1.5 Turning Animation
- Pac‑Man does **not** instantly flip direction.
- He performs a **rotation animation** (e.g., 180° when reversing).
- During rotation:
  - The mouth **does not chomp**.
  - Chomping resumes only after the turn completes.



## **2. Ghost Movement & Pathfinding**

### **2.1 Pathfinding Model**
- Ghosts use **A\*** pathfinding.
- They can:
  - Change direction at intersections.
  - Change direction mid‑path (optional per difficulty tier).

### **2.2 Intelligence Scaling via Recalculation Frequency**

Ghost “smartness” is controlled by how often they recalc their path:

- Level 1: every **1–2 seconds**
- Later levels: **higher frequency**, making them more reactive.

This is your main difficulty lever.

### **2.3 Additional Difficulty Levers**

- **Enable/disable mid‑path direction changes**.
- **Enable/disable intersection‑only turning**.
- **Ghost speed** increases per level.
- **Ghost behavior modes** (chase, scatter, flee) can be tuned per level.



## **3. Animation & Visual Effects**

### **3.1 Ghost Animation**

- Ghosts have a **flailing / cloth‑like motion** to emphasize floating.
- Each ghost has:
  - A **small circular shadow** beneath them.
  - A **colored glow/halo** matching their body color.
  - A **tinted shadow** (e.g., blue ghost → slightly blue shadow).

### **3.2 Lighting & Glow**

- Pac‑Man has a **soft glow** around him.
- Ghosts have a **faint neon halo**.
- Walls use **neon‑tube lighting**, giving a retro‑modern aesthetic.
- Scenes may use:
  - Bloom
  - Ambient lighting variations
  - Color‑themed palettes



## **4. Level Architecture & Storage**


### **4.1 Level Scriptable Object (LevelSO)**

**Responsibilities:**

- Stores the **ordered progression** of levels (linked list or array).
- For each level entry, stores:
  - **Scene name** to load.
  - **Prefab name** for the level layout.
  - Optional: placement coordinates, scaling.

**Does NOT store:**

- Pellet positions  
- Maze layout  
- Ghost/player parameters  
- Level logic  

Those belong to the **level prefab**.



### **4.2 Level Prefabs**

Each level is a **single prefab** containing:

- All **mazes** for that level.
- The **Level Manager** instance.
- Maze configuration components:
  - Pellet cells
  - Power pellet cells
  - Portal definitions
  - Maze connectivity
- Level‑specific parameters:
  - Ghost speeds
  - Pathfinding frequency
  - Player movement tuning
  - Lighting overrides (optional)

This keeps level data **self‑contained** and easy to iterate.



### **4.3 Scenes**

Scenes are used for **visual style**, not level logic.

Example:
- **Scene A** → Classic Pac‑Man look (Levels 1–5)
- **Scene B** → Custom neon/Esther‑style look (Levels 6+)

The LevelSO simply points multiple levels to the same scene if needed.



### **4.4 Persistent Systems**

These should live outside level prefabs and persist across loads:

- **Player Controller**
- **HUD Controller**
- **Score & Lives Manager**

They reset only on:
- Game Over
- Manual restart



## **5. Difficulty Strategy Summary**

Difficulty increases through:

1. **Ghost pathfinding frequency** (main lever).
2. **Ghost speed**.
3. **Turning flexibility** (intersection‑only → mid‑path allowed).
4. **Player forgiveness windows** (can shrink over time).
5. **Maze complexity** (more portals, tighter corridors).
6. **Lighting intensity** (optional aesthetic difficulty).
