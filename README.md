# Prince of Persia: Escape from the Palace

## Game Description

**Prince of Persia: Escape from the Palace** is a 2D side-scrolling action-adventure game built with the **iGraphics** library in C/C++. The Prince has to fight his way out of a palace and the caves beneath it across three hand-built levels, dodging guards, bats and piranhas and finally outrunning a rising flood to the escaping door.

Every level is timed, and your best time for each one is kept recorded.

## Features

- **Three complete levels**, each with different places of the palaces, backdrop and hazards.
- **Sword combat** against guards that chase, attack and patrol their own platforms.
- **A 13-frame walk cycle** for the Prince and for every enemy, in both directions.
- **Switches that act as checkpoints** - a fall returns you to the closest switch instead of to the start of the level.
- **Health hearts** at jump-reachable height, in random places and random numbers each time a level is opened.
- **Level 2's bats** - duck with `Q` as one bat comes near to head, or lose 20% of your health.
- **Level 3's flood** - free swimming, piranhas that can attack on you from anywhere in the water, and a climb back onto dry stone with `R`.
- **A Guardian boss** and a collapsing-floor escape run to finish the game.
- **A live level timer** with a progress bar that fills with your physical position in the level.
- **Persistent best records** per level, saved to a file and shown on their own page.
- Splash, main menu, story, instructions, credits, records, game-over, level-complete and victory screens.
- Background music and sound effects throughout.

## Project Details

IDE: Visual Studio 2013

Language: C, C++

Platform: Windows PC

Genre: 2D action adventure / platformer

Graphics: iGraphics (OpenGL + GLUT)

Resolution: 1350 x 680

## How to Run the Project

Make sure you have the following installed:

- **Visual Studio 2013**
- **iGraphics Library** (included in this repository)
- **GLUT** (`GLUT32.DLL` is included and must stay beside the executable)

### Option 1 - just play

Double-click **`Play.bat`** in the project root. It starts the game from the `iGame` folder, which is where all the artwork and sound live.

### Option 2 - build it yourself

- Open Visual Studio 2013.
- Go to File -> Open -> Project/Solution.
- Locate and select `iGame.sln` from the cloned repository.
- Click Build -> Build Solution.
- Run the program by clicking Debug -> Start Without Debugging.

The executable is built into the `iGame` folder on purpose: the game opens every image and sound by a relative path (`Assets/Player/l1.png`, `gamebgm.mp3`, ...) and needs `GLUT32.DLL` beside it, and all of that lives there.

## How to Play

### Controls

| Action | Key | Notes |
|---|---|---|
| Move left | `A` or Left Arrow | at a platform edge this becomes a jump |
| Move right | `D` or Right Arrow | at a platform edge this becomes a jump |
| Jump / climb up | `W` or Up Arrow | |
| Attack | `Space` | sword swing |
| Flip a switch | `E` or Down Arrow | stand next to it; you can also click it |
| Duck under a bat | `Q` | Level 2 |
| Swim up | `W` | Level 3, while in the water |
| Swim down | `S` | Level 3, while in the water |
| Swim left / right | `A` / `D` | Level 3, while in the water |
| Haul out of the water | `R` | Level 3, next to a wall or ledge |
| Skip to Level 2 | `P` | shortcut |
| Skip to Level 3 | `O` | shortcut |

Menus and buttons are operated with the **mouse**.

### The Levels

| Level | Setting | Ends when |
|---|---|---|
| **1** | Inside the palace | all 8 guards are defeated |
| **2** | The caves below, with bats and poison water | all 11 guards are defeated |
| **3** | Outside the palace - the final escape | you reach the escaping door |

### Game Rules

- The Prince starts each level on full health, shown by the bar in the top-left corner.
- Taking a hit from a guard, falling from a height, or drowning costs health.
- A bat that hits in Level 2 costs **20%** of your health - duck with `Q` to avoid it.
- In Level 3's water you lose **4% per second** just from being under, and **20% per second** while the piranhas have hold of you. Climb out with `R` before it runs out.
- A health heart restores **10%** of your health.
- Every switch you flip is a checkpoint. Fall after that and you come back to the switch, not to the start of the level.
- When your health reaches zero the run ends and the Game Over screen offers RETRY, MAIN MENU or EXIT.
- Each level is timed from the first moment of gameplay to the moment you complete it.
- The **lowest** time for a level is kept as that level's record. A slower run never replaces a faster one, and restarting a level never deletes a record.

### The Timer and the Progress Bar

The bar across the top of the gameplay screen does two separate jobs:

- The **numbers inside it** are the elapsed time for the current attempt, in `MM:SS.hh`.
- The **fill** is how far through the level you physically are, measured from your position in the place.

Your time and the level's best record are shown on the Level Complete screen, and the whole table is on the **RECORDS** page from the main menu.

## Screenshots

### Main Menu
<img src="screenshots/menu.png" width="640">

### Gameplay
<img src="screenshots/gameplay.png" width="640">

### Level Complete
<img src="screenshots/level_complete.png" width="640">

### Records
<img src="screenshots/records.png" width="640">

## Project Structure

```
Prince_of_Persia_Refactored/
|-- Play.bat                  launches the game
|-- iGame.sln                 Visual Studio 2013 solution
|-- README.md
|-- screenshots/
`-- iGame/
    |-- main.cpp              entry point
    |-- iGraphics.h           the graphics library
    |-- stb_image.h           PNG loading
    |-- GLUT32.DLL, *.lib     GLUT / OpenGL
    |-- *.mp3, attack.wav     music and sound effects
    |-- best_records.txt      created on first run
    |-- Header Files/
    |   |-- common.h          shared includes
    |   |-- game_types.h      structs
    |   |-- game_globals.h    constants, globals, screen states
    |   |-- next_level.h      setupLevel1 / 2 / 3
    |   |-- controls.h        input, physics, enemy AI, update loop
    |   |-- combat.h          attacking and damage
    |   |-- images.h          all drawing
    |   |-- records.h         level timer, progress bar and best records
    |   |-- sounds.h          music and sound effects
    |   |-- home.h            menu and button handling
    |   `-- reset.h           restarting a level
    `-- Assets/
        |-- Player/  Enemies/  Platforms/
        `-- Backgrounds/  Objects/  Water/  UI/
```

## Where Your Records Are Saved

`best_records.txt`, in the `iGame` folder next to the executable. It is created automatically the first time the game runs, and it looks like this:

```
LEVEL 1 35.81
LEVEL 2 72.43
LEVEL 3 48.29
```

Deleting the file simply clears every record.

## Project Contributors

1. Makdad Ibn Mannan
2. Adnan Mukid
3. Sudipta Roy
4. Litun Zira Iyesmin Prova

Proud students of **Ahsanullah University of Science and Technology**, Department of CSE.

## Youtube Link

[CSE 1200 Project: Prince of Persia - Escape from the Palace](https://www.youtube.com/)

## Project Report

[Project Report: Prince of Persia - Escape from the Palace](https://drive.google.com/drive/u/1/my-drive)
