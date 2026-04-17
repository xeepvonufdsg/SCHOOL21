# Project Team 01 — Go\_Bootcamp (Rogue Game)

**Summary:** In this team project, you'll develop a console-based roguelike game application in the Go programming language using the curses library (goncurses for Go) or similar, inspired by the classic 1980 game *Rogue*.

💡[Click here](https://new.oprosso.net/p/4cb31ec3f47a4596bc758ea1861fb624) to give us feedback on this project. It's anonymous and helps us improve the course. We recommend filling out the survey right after completing the project.

## Table of Contents

- [Chapter I](#chapter-i)
  - [Instructions](#instructions)
- [Chapter II](#chapter-ii)
  - [General Information](#general-information)
    - [Rogue 1980](#rogue-1980)
    - [Application Architecture](#application-architecture)
- [Chapter III](#chapter-iii)
  - [Task 0 — How Did We Get Here?](#task-0--how-did-we-get-here)
  - [Task 1 — The Essential Essences of the Game](#task-1--the-essential-essences-of-the-game)
  - [Task 2 — Energetic Gameplay](#task-2--energetic-gameplay)
  - [Task 3 — Generated World](#task-3--generated-world)
  - [Task 4 — Cozy 2D](#task-4--cozy-2d)
  - [Task 5 — Cartridge With Battery](#task-5--cartridge-with-battery)
  - [Task 6 — Bonus: You Shall Not Pass!](#task-6--bonus-you-shall-not-pass)
  - [Task 7 — Bonus: The Art of Balance](#task-7--bonus-the-art-of-balance)
  - [Task 8 — Bonus: Imagine You’re a Table](#task-8--bonus-imagine-youre-a-table)
  - [Task 9 — Bonus: Fully Three-Dee](#task-9--bonus-fully-three-dee)

## Chapter I

### Instructions

1. Throughout the course, you'll often feel uncertain and lacking information — that's part of the experience.\
   Remember, the repository and Google are always there for you. So are your peers and Rocket.Chat. Collaborate. Explore. Use common sense. Don’t be afraid to make mistakes.
2. Be critical of your sources. Cross-check. Think. Analyze. Compare.
3. Read tasks carefully — and re-read them again.
4. Examples deserve attention too. They might include things not explicitly described in the task itself.
5. You may encounter inconsistencies — when something in a task or example contradicts what you thought you knew. Try to figure it out. If you can't — write down your question and work through it as you go. Don’t leave questions unresolved.
6. If something seems unclear or impossible — it probably just feels that way. Break it down. Most parts will make sense on their own.
7. You’ll come across many different kinds of tasks. The bonus ones are for the curious and meticulous. They're harder and optional — but completing them will give you extra knowledge and experience.
8. When you ask for help, always make sure you understand the why, how, and what for. Otherwise the help won’t mean much.
9. Always push to the develop branch only. The master branch will be ignored. Work inside the src directory.
10. Your directory must not contain any files other than those specified in the tasks.

## Chapter II

### General Information

#### Rogue 1980

![RogueMap](assets/img_8861.png)

![Dungeon](assets/img_3519.png)

**Rogue** is a computer game developed in 1980 by the company Epyx. Its central theme is dungeon exploration. The game was extremely popular on university Unix systems in the early 1980s and gave rise to an entire genre known as **roguelikes**.

In *Rogue*, the player takes on a role typical for early fantasy RPGs — that of an adventurer. The game begins on the topmost level of an unmapped dungeon filled with monsters and treasures. As the player progresses deeper into the randomly generated dungeon, enemies grow stronger and exploration becomes increasingly difficult.

Each dungeon level consists of a 3x3 grid of rooms or dead-end corridors that might have been expected to lead to a room. Later versions of the game also include “mazes” — winding corridors with dead ends — in addition to regular rooms. Unlike most adventure games of that era, the layout of the dungeon and the placement of objects within it are procedurally generated. This made every playthrough unique and equally challenging for both new and experienced players.

The player has three attributes: **health**, **strength**, and **experience**. These can be increased through potions and scrolls or reduced by traps and cursed scrolls. A wide variety of magical potions, scrolls, wands, weapons, armor, and food results in highly diverse gameplay and multiple ways to win or lose.

#### Application Architecture

When developing applied projects involving data, business logic, and user interfaces, a **multi-layered architecture** is commonly used. The classical layered division can be represented as follows:

- **Presentation Layer** (View, UI)
- **Domain Layer** (Business Logic)
- **Data Source Layer** (Data Access)

**Separating logic into business and presentation layers will help organize the application's logic more effectively and decouple components with different levels of stability.**

In the **presentation** layer, place the code responsible for rendering the UI and handling user input. This is where interaction with the goncurses library (or similar) and the domain layer should be implemented.

The **domain** layer should encapsulate business logic that is independent of any frameworks. In this project, it includes the logic of game-related entities — such as the game itself, the player, enemies, levels, the map, and others — as well as the game mechanics. For example, the player's location and the logic for updating their position and attributes on the map must reside in this layer and then be passed to the presentation layer for rendering.\
Note that, according to the **clean architecture** principle, the business logic layer must not depend on the other layers. This is achieved by applying the **dependency inversion principle**.

To organize interaction between layers more efficiently, you may also use practices from the **MVC family of patterns** (such as MVP, MVVM, MVPVM, and others). These patterns separate logic (Model) from presentation (View) using intermediary layers like Controllers, Presenters, or View Models. Each language and framework has its own preferred implementations, but the underlying principles remain quite similar.

The **data layer** in this application is responsible for managing data — in this case, storing the history of previous games as well as the data for the current game session.

## Chapter III

### Task 0 — How Did We Get Here?

The game application:

- must have a console interface based on the goncurses library (or similar tcell, termui, ...);
- must be controlled via keyboard;
- must follow a well-designed, clean architecture with clear separation of layers;
- must implement the core mechanics of the classic *Rogue* (1980) game, with some simplifications (specific gameplay requirements are described in the following sections);
- if any aspects of gameplay design are not explicitly covered in this text, you may refer to the logic of the original 1980 mechanics as a valid basis.

### Task 1 — The Essential Essences of the Game

The game must follow the layer separation described in the "Application Architecture" section. The implementation should clearly distinguish between the **domain and gameplay layers**, the **rendering layer**, and the **data layer**.

To begin development, implement the **domain layer**, which should define the core entities of the game. Below is a list of recommended entities with basic attributes (required but not exhaustive):

- **Game session**
- **Level**
- **Room**
- **Corridor**
- **Character**, with attributes:
  - maximum health,
  - current health,
  - dexterity,
  - strength,
  - current weapon
- **Backpack**
- **Enemy**, with attributes:
  - type,
  - health,
  - dexterity,
  - strength,
  - hostility
- **Item**, with attributes:
  - type,
  - subtype,
  - health (number of health points restored, e.g., for food),
  - maximum health (number of health points increased, e.g., for scrolls and elixirs — also increases the current max health),
  - dexterity (points increased, for scrolls and elixirs),
  - strength (points increased, for scrolls, elixirs, and weapons),
  - value (for treasures)

### Task 2 — Energetic Gameplay

Implement the gameplay mechanics within the **domain layer**, independently of the presentation and data layers.

**Game Logic**

- The game must contain **21 dungeon levels**.
- Each dungeon level must consist of **9 rooms connected by corridors**, such that it is always possible to travel from any room to any other.
- Each room may contain enemies and items — except for the **starting room**.
- The player controls character movement, can interact with items, and fight enemies.
- The goal on each level is to find the passage to the next one, ultimately progressing through all **21 levels**.
- At the beginning of each level, the player starts in a **random location within the starting room**, which is **guaranteed to be free of enemies**.
- When the main character dies, the game resets and everything returns to the beginning.
- As the player progresses to each new level:
  - the **number and difficulty of enemies increases**,
  - the **amount of useful items decreases**,
  - the **amount of treasure dropped by defeated enemies increases**.
- After each run (whether successful or not), the player's result must be **recorded in a leaderboard**, showing:
  - the **deepest level reached**,
  - the **amount of treasure collected**.
- The leaderboard must be **sorted by treasure collected**, in descending order.
- The entire game must operate in **turn-based mode**: each player action triggers enemy actions.
- **Nothing in the game world moves until the player makes a move.**

**Character Logic**

- The **health** attribute represents the character’s current health.\
  When health reaches **0 or below**, the game must end.
- The **maximum health** attribute indicates the upper limit of health that can be **restored by consuming food**.
- The **dexterity** attribute affects the **hit probability formulas** — both for enemies hitting the character and the character hitting enemies.
- The **strength** attribute determines:
  - the **base unarmed damage** dealt by the character,
  - and contributes to the **damage formula** when using weapons.
- Defeating an enemy rewards the character with **treasure**, based on the enemy’s difficulty.
- The character can **pick up items** and store them in their **backpack**, then **use** them later.
- When used, each item can **temporarily or permanently modify** one or more of the character’s attributes.
- Upon reaching the level exit, the character **automatically progresses** to the next level.

**Enemy Logic**

Each enemy has attributes similar to the player’s: **health**, **dexterity**, and **strength**, plus an additional attribute — **hostility**.

The **hostility** attribute determines the **distance at which the enemy starts chasing the player**.

There are **five types of enemies**, each with unique traits and behavior patterns:

- **Zombie** (display: green z)
  - Low dexterity
  - Medium strength and hostility
  - High health
- **Vampire** (display: red v)
  - High dexterity, hostility, and health
  - Medium strength
  - **Reduces the player’s maximum health** upon a successful attack
  - The **first hit against a vampire always misses**
- **Ghost** (display: white g)
  - High dexterity
  - Low strength, hostility, and health
  - Constantly **teleports within the room**
  - Periodically **becomes invisible** unless in active combat with the player
- **Ogre** (display: yellow O)
  - Moves two tiles per turn within the room
  - Very high strength and health
  - **Rests for one turn after each attack**, then **counterattacks with certainty**
  - Low dexterity
  - Medium hostility
- **Snake-Mage** (display: white s)
  - Very high dexterity
  - Moves diagonally across the map, constantly switching direction
  - Each successful attack has a chance to **put the player to sleep for one turn**
  - High hostility

Each enemy type follows its own **movement pattern** within a room.

When the player enters the **hostility range** of a monster, the monster begins to **chase the player** by following the shortest path using adjacent tiles.

If the player is within the aggression radius but **there is no path** to reach them, the monster continues to move randomly following its own movement pattern.

**Environment Logic**

- Each item type has its own effect:
  - **Treasures** — have value, accumulate over time, and contribute to the final score. Treasures can only be obtained by **defeating enemies**.
  - **Food** — restores **health** by a certain amount.
  - **Elixirs** — **temporarily increase** one of the character’s attributes: dexterity, strength, or maximum health.
  - **Scrolls** — **permanently increase** one of the attributes: dexterity, strength, or maximum health.
  - **Weapons** — have a **strength** attribute.
- When equipped, the **damage calculation formula changes** accordingly.
- When the **maximum health** increases, the **current health** is also increased by the same amount.
- If an elixir effect expires and the character’s health drops to **0 or below**, the character’s health must be reset to the **minimum possible positive value** in order to continue the game.
- The **backpack** holds all item types.
- When the character steps on an item, it is automatically added to the backpack — **if there is space**.
  - The backpack can hold up to **9 items of each type**.
  - **Treasures** are cumulative and stored in a **single slot**.
- **Food, elixirs, and scrolls** are **consumed upon use**.
- **Weapons**, when replaced, must be **dropped on the floor to an adjacent tile**.
- Each dungeon level has content that **scales with its depth**:
  - The deeper the level, the more difficult it becomes.
  - A level consists of **rooms**.
  - Rooms are connected by **corridors.**
  - Rooms contain **enemies** and \*\*items.
  - Both enemies and the player can move between rooms and corridors.
  - Each level contains a **guaranteed passage to the next**.
  - Exiting the final level ends the game.

**Combat Logic**

- Combat is processed in **turn-based mode**.
- An attack is initiated by moving the character **toward an enemy**.
- Combat begins **upon contact** with the enemy.
- Each strike is resolved in **sequential stages**:
  - **Hit check** — A probabilistic check is performed to determine whether the attack lands. The chance to hit depends on the **dexterity** of the attacker and the target.
  - **Damage calculation** — If the hit is successful, the **damage** is calculated based on the attacker's **strength** and any active **modifiers** (such as weapon stats).
  - **Damage application** — The calculated damage is **subtracted from the target’s health**. If health drops to **0 or below**, the target — whether enemy or player — **dies**.
- When an enemy is defeated, a **random amount of treasure** is dropped, based on the enemy’s **hostility**, **strength**, **dexterity**, and **health**.

### Task 3 — Generated World

- Implement the **level generation module** within the **domain layer**.
- Each level must be logically divided into **9 sections**, with a **randomly generated room** placed in each section.
- Rooms must vary in **size and position**, generated **randomly**.
- Rooms are connected by **corridors**, also generated procedurally.
- Corridors have their own **geometry**, and characters must be able to move through them.
- Therefore, their **coordinates must also be generated and stored**.
- During generation, you must ensure that the **resulting graph of rooms is connected** and contains **no structural errors**.
- Each level must include:
  - one **starting room**, where the game session begins;
  - one **exit room**, containing a special tile — when touched, it **transfers the player to the next level**.
- An example implementation of level generation can be found in the code-samples folder.

### Task 4 — Cozy 2D

Implement game rendering in the **presentation layer** using goncurses (or similar), based on the necessary **domain entities**.

**Rendering**

- **Environment rendering**: walls, floor, wall openings, and corridors between rooms.
- **Actor rendering**: player character, enemies, and collectible items.
- **Interface rendering**: game UI, including status panel, inventory, and basic menus.
- **Fog of War** — the rendered scene must depend on the current game state:
  - Unexplored rooms and corridors are **not displayed**.
  - Previously explored rooms where the player is **not present** are displayed as **walls only**.
  - The room containing the player displays **walls, floor, actors, and items**.
  - When standing near a room's entrance from a corridor, fog is lifted **only for the field of view** — calculated using **Ray Casting** and **Bresenham's algorithm** to determine the visible area.
- An example rendering implementation can be found in the code-samples folder.

**Controls**

- Character controls:
  - Move with the **WASD keys**
  - Use a **weapon** from the backpack: h
  - Use **food** from the backpack: j
  - Use an **elixir** from the backpack: k
  - Use a **scroll** from the backpack: e
- When using any item from the backpack, the game must **display a list of items of that type**, asking the player which one to select (1–9).
- When selecting a weapon, there must also be an option to **unequip the weapon** without removing it from the backpack (thus, for weapons, the choice range is 0–9).

**Statistics**

- The game must collect and display a **separate statistics view** for all playthroughs, sorted by the **total amount of treasure collected**.
- The stats must include:
  - total treasure collected
  - deepest level reached
  - number of defeated enemies
  - amount of food consumed
  - number of elixirs drunk
  - number of scrolls read
  - total hits dealt and received
  - number of tiles traveled

### Task 5 — Cartridge With Battery

- Implement the **data layer**, responsible for saving and loading the player’s game progress to and from a JSON file.
- After each level is completed, the game must **save the current statistics and the level number reached**.
- **After restarting the game, if the player wants to continue the last saved session, the levels must be generated according to the saved data, and the player's progress must be fully restored (accumulated points, current attribute values), i.e., all session information must be recovered, down to the position and properties of individual entities.**
- All statistics from previous playthroughs must also be preserved.
- When the player views the **leaderboard**, the **best playthroughs** should be shown (regardless of whether the run was completed or not).

### Task 6 — Bonus: You Shall Not Pass!

- Generate **doors** between rooms and corridors, along with **keys** to unlock them.
- Implement a **colored key system**, inspired by the classic *DOOM*.
  When solving this task, use **modified depth-first or breadth-first search algorithms** to verify that:
  - all keys are accessible,
  - the level is **free from softlocks** (situations where progress becomes impossible due to design flaws).

### Task 7 — Bonus: The Art of Balance

Add a **dynamic difficulty adjustment system**.

- If the player progresses too easily, **increase the difficulty**.
- If the player struggles, the game may provide **slightly more helpful items**\
  (e.g., more healing items if the player often loses health),\
  and **reduce the number or difficulty of enemies**.

### Task 8 — Bonus: Imagine You’re a Table

Add a new enemy type: the **Mimic** (m, white), which **mimics items**.

- High dexterity
- Low strength
- High health
- Low hostility

### Task 9 — Bonus: Fully Three-Dee

Add a **3D rendering mode**, in which:

- The **main view switches to a first-person 3D perspective**.
- The **2D view remains available** as a **mini-map** in the corner of the screen.
- Controls are adapted accordingly:
  - W — move forward
  - S — move backward
  - A — turn left
  - D — turn right
- To render rooms and corridors in 3D, use **Ray Casting** and the goncurses library (or similar).\
  Walls in rooms and tunnels must have **textures**, so that the player's movement is **visually perceptible**.
- An example implementation of 3D rendering can be found in the code-samples folder.