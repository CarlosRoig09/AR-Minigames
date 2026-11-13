# AR-Minigames

A project I made for testing and practice my Vuforia Engine skills on Unity. It also uses the gyroscope technology to perform movement actions on game. 

##Github Repository 
This github Repository contains the APK to play the game located in the folder **Android APK*, the AR Targets to be able to play the game and the unity package linked on the **Unity package* pdf.

# Game Design

## Objective

Obtain all the puzzle pieces to complete the main puzzle, which consists of fitting the pieces into a three-dimensional cube.

To obtain the pieces, you must complete two types of minigames across two difficulty levels. The theme is centered around three different actions:

* **Movement:** *(Minigame not finished)*
* **Rotation:** Sword minigame.
* **Scale:** Trampoline minigame.
* **All:** The puzzle minigame combines all mechanics.

Each minigame is located on a specific poster image, located in the **AR Targets** folder

---

## Mechanics

First, here are the general mechanics:

* **Movement:** The clicked shape (finger held down on it) follows the position of that finger. This is achieved using a collider and a raycast projected from the finger via the camera; the raycast's collision point with the collider determines the object's local position.
* **Rotation:** Rotation works using the mobile device's gyroscope. You can perform two movements with the phone: on the **Roll** axis and on the **Yaw** axis. This action rotates shapes along those respective axes. If you deselect the shape, it retains its new rotation as the baseline, allowing you to rotate the object from that same orientation using the phone's initial position. You can reset the rotation to its original state by tapping the **Return Rotation** button.
* **Scale:** The object is scaled based on the position of two fingers. It is not proportional to the distance between the fingers; instead, the scale increases at a set speed ($X$). The direction of this speed depends on whether the initial distance between the fingers is greater or less than the final distance. Scaling is capped at a minimum and maximum size.

> **REMEMBER:** FOR ROTATION AND SCALING, YOU MUST SELECT THE SHAPE WITH ONE FINGER FIRST. OTHERWISE, IT WILL NOT WORK.

---

## Minigames

* Every minigame—except the puzzle—has an **Easy** and a **Hard** mode. The difference between them lies in adjusted parameters.
* Losing sight of the **ImageTarget** restarts the game, except if you already finished it. 
* If you lose, you can retry the level.
* Once won, you earn a puzzle piece, and the minigame cannot be replayed unless you perform a full game **restart**.

### Sword Minigame

A wooden plank spawns every $X$ seconds. Your objective is to use the rotation mechanic to slice along the line separating the two sides of the plank.

You must align the sword on the **Roll** axis and slice the plank using the **Yaw** axis.

* **Victory Condition:** Slice the final plank, which contains a puzzle piece.
* **Defeat Condition:** Allow a plank to get too close to the sword's hilt.
* **Easy vs. Hard Mode Differences:**
  * Number of planks
  * Spawn frequency
  * A new plank type
  * Speed

### Trampoline Minigame

A ball drops onto a trampoline. Depending on the trampoline's scale, the ball will bounce with greater or lesser force: if the scale is smaller, the ball bounces higher; if it is larger, it bounces lower. The goal is for the ball to get as close as possible on each bounce to a target that changes position at the peak of every bounce.

The ball bounces a set number ($X$) of times. Depending on the distance between the ball and the target at the peak of the bounce, the player earns different points:
* **5 points** if it is very close.
* **3 points** if it is close.
* **1 point** if it is not very close.

* **Victory Condition:** Beat the target score, earning a puzzle piece.
* **Defeat Condition:**
  * Letting the ball fall off.
  * Failing to beat the target score.
* **Easy vs. Hard Mode Differences:**
  * Target score required.

### Final Minigame: Puzzle

After beating the other minigames, you will have all four puzzle pieces needed to complete the cube.

The objective is to rotate the faces of the cube to find slots that match the pieces, and rotate the pieces so they face the specific side where they fit. Their exact rotation does not need to match—they simply need to face the side of the shape containing the slot. Additionally, the piece's scale must match or be similar to the size of the slot.

* **Victory Condition:** Place all pieces into their slots.
* **Defeat Condition:** None.

Once completed, the game ends and gives you the option to reset everything and start over—an option also available in the **Help** menu.
 
