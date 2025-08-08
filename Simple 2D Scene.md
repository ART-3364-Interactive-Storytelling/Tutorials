# Creating a 2D Scene with a Solid Background (with Intro to C#)

## Objective

By the end of this tutorial, you will:

- Set up a simple 2D Unity scene
- Add a solid-colored background
- Create and move a simple sprite
- Write a **basic C# script** to make your sprite move with arrow keys

This tutorial is beginner-friendly and assumes **no prior coding experience**—just a willingness to explore!

---

## Prerequisites

- Unity Hub and **Unity 6.x** installed
- A basic understanding of using your computer (clicking, dragging, typing)
- A desire to learn 

---

## Step-by-Step Instructions

### 1. Create a New 2D Unity Project

1. Open **Unity Hub**
2. Click **“New Project”**
3. Choose the **2D Built-in Render Pipeline** template.
4. You may have to download the template if this is your first time using it.
5. Name your project something like `Simple2DScene`
6. Choose a folder location and click **Create project**

---

### 2. Set a Solid Background Color

1. In the **Hierarchy**, click on the `Main Camera`
2. In the **Inspector** window:
   - Find the **Camera** component
   - Change **Clear Flags** from `Skybox` to `Solid Color`
   - Click the color box to pick a background color (e.g., light blue)

> 📝 This sets the camera's background to a solid color.

---

### 3. Add a Sprite (Visual Object)

1. In the **Hierarchy**, right-click → `2D Object` → `Sprite` -> MySprite
2. Rename the new object to `Player`
3. If you want a different shape, in the **Inspector**:
   - Click the small circle next to the **Sprite** field
   - Choose a built-in sprite like `Circle` or `Square`
4. Use the **Rect Tool** to resize or reposition it as you like

---

### Create Your First C# Script

#### Create the Script

1. In the **Project** window, right-click in the `Assets` folder
2. Select `Create` → `C# Script`
3. Name the script `PlayerMovement`
4. Drag the script onto the `Player` object in the **Hierarchy**

#### Edit the Script

1. Double-click `PlayerMovement.cs` to open it in Visual Studio (or your default editor)
2. Replace the contents with the following:

```csharp
using UnityEngine;

public class PlayerMovement : MonoBehaviour
{
    public float moveSpeed = 5f;

    void Update()
    {
        float moveX = Input.GetAxis("Horizontal");
        float moveY = Input.GetAxis("Vertical");

        Vector3 move = new Vector3(moveX, moveY, 0);
        transform.position += move * moveSpeed * Time.deltaTime;
    }
}
```
### What This Code Does

This script lets you move the sprite using the arrow keys or WASD. Here's a breakdown of what each part does:

#### Explanation:

| Element                           | What It Does                                                                 |
|----------------------------------|------------------------------------------------------------------------------|
| `moveSpeed`                      | A variable that sets how fast the sprite moves. You can adjust it in Unity. |
| `Update()`                       | A special function that Unity runs every frame. It's where we check for input. |
| `Input.GetAxis("Horizontal")`    | Detects left and right input (A/D or Left/Right arrow keys).                |
| `Input.GetAxis("Vertical")`      | Detects up and down input (W/S or Up/Down arrow keys).                      |
| `Vector3 move`                   | Combines horizontal and vertical input into one direction.                  |
| `transform.position += move ...` | Moves the sprite on screen by changing its position every frame.            |
| `Time.deltaTime`                 | Ensures smooth movement regardless of how fast your computer runs.          |

> 💡 **Tip:** You can modify `moveSpeed` in the Unity Inspector to make the sprite faster or slower.

> ℹ️ **C# Note** The f after 5 in the assignment statement for moveSpeed tells C# that the number is a **floating point** number, the programming name for a **real number** or decimal.  A moveSpeed of 5 without the f would be an **integer** or **whole number**

#### Detailed Script Explanation
Click [here](https://github.com/bakkertj/Interactive-Storytelling/blob/main/Tutorials/Simple%202D%20Scene%20Script.md) for a more detailed line-by-line explanation of the script.

---

### ▶ Run the Scene

1. Click the **Play** button ( ▶ ) at the top center of Unity.
2. Use the **arrow keys** or **WASD** to move your player sprite.
3. Click **Play** again to stop the game.

---
### Modifying Values in the Inspector

Notice when you click, in the hierarchy, on an object with an attached script the inspector has entries for every ```public``` variable

<img width="1538" height="934" alt="Simple2DInspector" src="https://github.com/user-attachments/assets/ddbe4570-4cd3-4b8d-882d-af2075bd509c" />

You can modify the initial value for ```moveSpeed``` in the inspector and it will be reflected in the code automatically.

#### Inspector "nicifying" 
The reason the Unity Inspector displays your variable as “Move Speed” (with a space) even though it’s written as ```moveSpeed``` in your code is because of Unity’s built-in naming convention logic for public fields.

This variable is public, so Unity automatically exposes it in the Inspector.
* Unity’s Inspector takes the variable name (```moveSpeed```) and converts it into a human-readable label:
* It inserts spaces before capital letters.
* So ```moveSpeed``` → ```Move Speed```

This process is known as “nicifying” the variable name.

---

### What You’ve Learned So Far

| Concept        | What You Did                                                     |
|----------------|------------------------------------------------------------------|
| Scene Setup    | Created a 2D project and set a solid background color.           |
| Sprite Usage   | Added a simple shape to represent a player object.               |
| Scripting      | Wrote and attached your first C# script to control movement.     |
| Input Handling | Used keyboard input to move your sprite around the scene.        |

---

### Ready for Next Steps?

If you're feeling confident, try one of these beginner-friendly challenges:

- Replace the square sprite with your own artwork.
- Add a background image to your scene.
- Add a second object and make it move in a different way.
- Write a script that plays a sound when the player moves.

---
