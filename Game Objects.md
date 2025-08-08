# Unity GameObjects: Structure and Components

## What Is a GameObject?

In Unity, a **GameObject** is the fundamental entity in the scene hierarchy. It represents anything that can exist in the scene — from a character or tree to a light, UI element, or empty container.

A GameObject by itself does nothing. It becomes meaningful by **attaching components** that define its behavior, appearance, physics, or interaction with the game world.

---

## Anatomy of a GameObject

Every GameObject in Unity **always contains a `Transform` component** by default. All other behavior is added via additional components.

### Default GameObject Structure

When you create a new GameObject (via `GameObject → Create Empty`), Unity automatically includes:

| Component       | Purpose                                        |
|----------------|------------------------------------------------|
| **Transform**   | Required. Defines position, rotation, and scale in world or local space. |

All GameObjects — even cameras, lights, and UI elements — contain a `Transform`.

---

## Adding Components

Unity follows a **component-based architecture**. You attach components to a GameObject to give it specific functionality.

Example:
```csharp
GameObject player = new GameObject("Player");
player.AddComponent<Rigidbody>();
player.AddComponent<MeshRenderer>();
```

In the Unity Editor, this is equivalent to selecting a GameObject and clicking “Add Component” in the **Inspector**.

## Commonly Used Built-in Components

1. **Transform (always present)**
* Holds position (Vector3), rotation (Quaternion), and scale (Vector3)
* Supports parenting and hierarchy (scene graph structure)

2. **Renderer Components**

|   Component    | Description |
|----------------|------------------------------------------------|
|  MeshRenderer  | Renders a 3D mesh using a MeshFilter and Material
| SpriteRenderer | Renders 2D sprites in a 2D scene
| SkinnedMeshRenderer | Used for animated character models
| LineRenderer, TrailRenderer | Draws lines or trails in 3D space

3. **Collider Components**[^1]

| Component | Description
|----------------|------------------------------------------------|
| BoxCollider | Axis-aligned box collider (3D)
| SphereCollider | Spherical collider
| MeshCollider | Collider shaped like a mesh
| CircleCollider2D | 2D circle for 2D physics
| PolygonCollider2D | Arbitrary 2D shape

4. **Physics Components**

| Component | Description
|----------------|------------------------------------------------|
| Rigidbody | Enables 3D physics simulation
| Rigidbody2D | Enables 2D physics simulation
| CharacterController | A built-in movement controller for characters

5. **Audio Components**

| Component | Description
|----------------|------------------------------------------------|
| AudioSource | Plays audio clips on the GameObject
| AudioListener | Usually attached to the Main Camera; hears sounds in the scene

6. **Camera and Light Components**

| Component | Description
|----------------|------------------------------------------------|
| Camera | Renders the scene to the screen
| Light | Emits light into the scene
| FlareLayer, Halo, LensFlare | Optional light effects

7. **UI Components (Canvas-based)**

| Component | Description
|----------------|------------------------------------------------|
| Canvas | Root of all UI rendering
| Text / TextMeshPro | Displays text in UI
| Image | Displays a texture (sprite)
| Button, Slider, Toggle, etc. | Interactive UI elements
| RectTransform | Specialized Transform for UI layout

💡 UI GameObjects use RectTransform instead of Transform.

## Custom Components

### MonoBehaviour Scripts

You can define your own components by creating a script that extends MonoBehaviour. These are added just like built-in components.

```csharp
public class PlayerController : MonoBehaviour
{
    void Update()
    {
        // Handle player input
    }
}
```

Attach this script to a GameObject to give it player control behavior.

## MonoBehaviour Lifecycle Methods

If a component inherits from MonoBehaviour, it can use Unity’s lifecycle methods:
*	```Awake()``` — Called when the component is initialized
* ```Start()``` — Called before the first frame update
* ```Update()``` — Called once per frame
* ```FixedUpdate()``` — Called on a fixed interval (used for physics)
* ```OnEnable()``` / ```OnDisable()``` — Called when the component is toggled
* ```OnDestroy()``` — Called before the GameObject is destroyed



[^1]:Note: Colliders alone do not move — they must be paired with Rigidbody components.

   
