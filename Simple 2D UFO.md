# 2D Scene with a UFO Sprite

## Objective

By the end of this tutorial, you will:

- Set up a simple 2D Unity scene
- Add a star-filled background
- Write a **C# script** to move a UFO sprite back and forth
  
---

## Prerequisites

- Unity Hub and **Unity 6.x** installed
- Completion of [Simple 2D Scene](https://github.com/bakkertj/Interactive-Storytelling/blob/main/Tutorials/Simple%202D%20Scene.md) Project

---

## Step-by-Step Instructions

### 1. Create a New 2D Unity Project

1. Open **Unity Hub**
2. Click **“New Project”**
3. Choose the **2D Built-in Render Pipeline** template.
4. You may have to download the template if this is your first time using it.
5. Name your project something like `SpaceInvader`
6. Choose a folder location and click **Create project**

---
### 2. Add the Texture Assets

1. Download:
   * [256x256-UFO.png](https://github.com/bakkertj/Interactive-Storytelling/blob/main/Tutorials/Assets/256x256-UFO.png)
   * [Star Background.png](https://github.com/bakkertj/Interactive-Storytelling/blob/main/Tutorials/Assets/Star%20Background.png)
   * [farm.png](https://github.com/bakkertj/Interactive-Storytelling/blob/main/Tutorials/Assets/farm.png)
3. Right-click the Assets folder in the hierarchy and select "Import New Asset" and import all three sprites
4. Select each image in the **Project** tab, and in the **Inspector**, set:
* Texture Type: Sprite (2D and UI)
* Filter Mode: Point (no filter)
* Compression: None

The Inspector for the UFO should look like:

<img width="462" height="526" alt="Screenshot 2025-08-06 at 6 12 47 PM" src="https://github.com/user-attachments/assets/ae10d457-5129-4e2c-b4a8-11b34fa81eb7" />

5. Click apply for each
6. Drag the UFO sprite into the **Hierarchy** to create a GameObject. Rename it to UFO.
7. In the **Inspector**:
* Set the scale of the UFO to 0.25, 0.25, 0.25
* Set the Y position of the UFO to 2

It should look like:

<img width="470" height="179" alt="Screenshot 2025-08-07 at 9 06 57 AM" src="https://github.com/user-attachments/assets/7ddfe2e7-b43a-425a-98d8-94e6a356357c" />

  
8. Drag the Starry Background sprite into the **Hierarchy** to create a GameObject. Rename it to Star Background.
9. In the **Inspector**:
* Set the Position to 0, 0, -10 [^1]
* Set the scale of the Star Background sprite to 1.5, 1.5, 1.5

It should look like:

<img width="472" height="253" alt="Screenshot 2025-08-07 at 9 11 11 AM" src="https://github.com/user-attachments/assets/efe249ee-b3be-4e90-8ed3-c56ad3641596" />

10. Drag the Farm sprite into the **Hierarchy** to create a GameObject. Rename it to Farm.
11. In the **Inspector**:
* Set the Position of the Farm sprite to 0, -2.8, 0
* Set the Scale of the Farm sprite to 1.2, 1.0, 1.0

It should look like:

<img width="472" height="186" alt="Screenshot 2025-08-07 at 9 13 50 AM" src="https://github.com/user-attachments/assets/6573f4af-2af3-4738-89d5-23d5701e9257" />


### Create the UFO Script

#### Create the Script

1. In the **Project** window, right-click on **Assets** → Create → MonoBehaviour Script
2. Name it UFOMovement
3. Drag the script onto your UFO GameObject in the **Hierarchy**


#### Edit the Script

1. Double-click `UFOMovement.cs` to open it in Visual Studio (or your default editor)
2. Replace the contents with the following:

```csharp
using UnityEngine;

public class UFOMovement : MonoBehaviour
{
    public float speed = 2f;         // Movement speed
    public float range = 8f;         // How far left and right it moves from its start point

    private Vector3 startPos;        // Initial position
    private bool movingRight = true;

    void Start()
    {
        startPos = transform.position;
    }

    void Update()
    {
        if (movingRight)
        {
            transform.position += Vector3.right * speed * Time.deltaTime;

            if (transform.position.x > startPos.x + range)
                movingRight = false;
        }
        else
        {
            transform.position += Vector3.left * speed * Time.deltaTime;

            if (transform.position.x < startPos.x - range)
                movingRight = true;
        }
    }
}
```

### ▶ Run the Scene

<img width="1582" height="978" alt="Screenshot 2025-08-07 at 9 54 02 AM" src="https://github.com/user-attachments/assets/c05c9949-39dd-48f5-9011-6a023c45164e" />

1. Click the **Play** button ( ▶ ) at the top center of Unity.
2. Use the **arrow keys** or **WASD** to move your player sprite.
3. Click **Play** again to stop the game.

### Extra Fun
* Want a sine wave movement? Use Mathf.Sin(Time.time) with the y portion of the Vector3. ```float yOffset = Mathf.Sin(Time.time * speed) * amplitude;```
* Want diagonal motion? Add vertical movement (Vector3.up) too.
* Want a wave of UFOs? Duplicate the UFO GameObject and offset their positions in the Inspector.
---

[^1]: In Unity 2D: Sprite Rendering Is Controlled by Two Systems
    1. Z-Position (Transform.position.z)
    2. Order in Layer (on SpriteRenderer)
    In Unity 2D, Z-position has no effect on rendering order unless you’re using a custom shader or working in 3D mode.

    By default, Unity ignores the Z-axis for draw order in 2D. It uses:
    * Sorting Layer
    * Order in Layer

    So Why Do We Set the Position to Z = 10?

    The Z-position only affects spatial placement, like:
    * Whether the camera can see the object (because the camera has a Z position)
    * Raycasting and physics (depending on depth)
    * Parallax effects (if you manually scroll objects at different Z)

    But it does NOT control render order unless you go full 3D.
