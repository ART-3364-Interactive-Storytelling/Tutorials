# Unity 2D Camera Overview

In Unity, the **Camera** is a fundamental component that determines what the player sees during gameplay. In 2D games, the camera operates in a top-down orthographic mode, which eliminates perspective and keeps the view flat—ideal for side-scrollers, top-down shooters, and tile-based games.

---

## What Is the Camera?

A **Camera** in Unity is a GameObject with a `Camera` component attached. It functions as the "eye" through which the game world is viewed. In 2D, this typically means showing a portion of the world along the X and Y axes while ignoring the Z axis for perspective.

### Key Properties of a 2D Camera:

| Property         | Description |
|------------------|-------------|
| **Projection**   | Should be set to **Orthographic** for 2D games. |
| **Size**         | Determines how much of the world is visible vertically. |
| **Position (X,Y,Z)** | Controls what portion of the world is shown. |
| **Clear Flags**  | Determines how the background is rendered. |
| **Culling Mask** | Selects which layers the camera can see. |

---

## Coordinate System in Unity 2D

Unity’s 2D coordinate system operates on:

- **X axis**: horizontal (left to right)
- **Y axis**: vertical (bottom to top)
- **Z axis**: used for **layering** objects (depth)

Unity uses **world units**, where 1 unit typically represents 1 meter in real-world scale.

### Example:

- Background sprite: at position `(0, 0, 10)`
- Foreground sprite: at position `(0, 0, 0)`
- Camera: at position `(0, 0, -10)`

In **Orthographic** mode, Z-position does not affect how large objects appear on screen, only their draw order.

---

## Orthographic Size

In 2D, the **Orthographic Size** is one of the most important settings. It defines the **vertical half-size** of the camera’s visible area in world units.

### Example:

If the orthographic size is `5`, the total visible height is `10` world units. The width is determined by:

```
Visible Width = (2 * Orthographic Size) * (Screen Width / Screen Height)
```

## Camera Position: 

While the world origin (0,0,0) is typically at the screen center, the actual camera position can influence what is visible. If the camera itself is moved from (0,0,0), then the visible center of the screen will shift accordingly.

### Example:
Combining the two sections above, if the orthographic size is `5`, the top of the screen is a Y-position of 5 and the bottom of the screen is a Y-position of -5

---

## Sorting Layers and Order in Layer

When multiple 2D objects share the same X/Y position, Unity uses **Sorting Layers** and **Order in Layer** to determine which object appears in front.

- Use **Sorting Layers** to define logical groups like `Background`, `Midground`, and `Foreground`.
- Use **Order in Layer** to fine-tune the draw order within a given layer.

---

## Moving the Camera

You can move the camera to follow the player or another object:

```csharp
public class CameraFollow : MonoBehaviour
{
    public Transform target;

    void LateUpdate()
    {
        transform.position = new Vector3(target.position.x, target.position.y, transform.position.z);
    }
}
```

This keeps the camera centered on the target while maintaining the Z-axis value.

---

## Summary

- Use **Orthographic Projection** for 2D games.
- Set the **Z position** of the camera behind the objects (e.g., -10).
- Use **Orthographic Size** to control the visible area.
- Use **Sorting Layers** and **Order in Layer** for depth control.
- Attach a simple follow script to create dynamic camera behavior.

---

## Additional Tips

- Lock the camera's **rotation** to (0, 0, 0) for 2D games.
- Adjust the **camera bounds** to prevent showing out-of-bounds areas.
- For parallax effects, vary object positions along the Z-axis and use different movement speeds.
