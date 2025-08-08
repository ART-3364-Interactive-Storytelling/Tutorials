# Understanding Unity Scenes

## What Is a Scene in Unity?

A **Scene** in Unity is a self-contained environment that holds everything that appears in a specific part of your game or application. Think of it as a level, screen, or state — such as a title screen, gameplay level, menu, or credits roll.

Scenes are the fundamental unit of organization in Unity and are saved as `.unity` files in the project's `Assets` folder.

---

## Key Concepts

### GameObjects in Scenes

Each Scene contains a hierarchy of **GameObjects**, which may include:

- Visual objects (e.g., Sprites, 3D models)
- UI elements (e.g., Buttons, Text, Canvas)
- Cameras and Lights
- Logic and behavior via attached scripts (MonoBehaviours)
- Environment elements (e.g., backgrounds, terrain)

GameObjects in a Scene form a tree structure using **Transforms**, which define position, rotation, and scale.

### Scenes as States

Scenes often represent **discrete application states**:

| Scene Type       | Purpose                                   |
|------------------|--------------------------------------------|
| Title Scene      | Game title and logo                       |
| Menu Scene       | Navigation: Start, Load, Exit, etc.       |
| Game Scene       | Actual gameplay environment               |
| Pause Scene      | Overlay for pause menu                    |
| Credits Scene    | Displays developer and contributor info   |
| Cutscene Scene   | Plays cinematic or transition sequences   |

---

## Scene Management

### Loading Scenes

Scenes are loaded via the `SceneManager` API in the `UnityEngine.SceneManagement` namespace.

#### Single Scene Load (Replaces Current Scene)

```csharp
SceneManager.LoadScene("Level1");
```

This unloads the current scene and loads Level1.

#### Additive Scene Load (Combines Scenes)
```
SceneManager.LoadScene("UIOverlay", LoadSceneMode.Additive);
```

This loads UIOverlay on top of the currently loaded scene. Additive scenes are useful for persistent UIs, streaming level sections, or modular scene composition.

#### Build Settings
Before you can load a scene in code, it must be added to:
```
File → Build Settings → Scenes In Build
```

### Scene Hierarchy and Workflow

#### Editing Scenes

You can open and edit a scene in the Unity Editor. When a scene is active:
* Its hierarchy of GameObjects is visible and editable
* You can test gameplay by pressing Play

Unity allows you to switch scenes in the Editor or even open multiple scenes at once (for additive workflows).

#### Saving Scenes

Scenes are saved explicitly using File → Save Scene or Ctrl+S. It’s common to save multiple scenes in subfolders like:
```
Assets/Scenes/
Assets/Scenes/Menu/
Assets/Scenes/Levels/
```

### Best Practices
* Keep UI and Game logic in separate scenes for modularity
* Use additive scenes for persistent elements like global managers or HUDs
* Create a bootstrap scene to initialize systems like audio, analytics, and loading
* Use prefabs for reusable objects across scenes
* Clean up memory-heavy scenes when transitioning to avoid leaks

### Scene Example Workflow
```
[BootstrapScene]
  └─ GameManager (DontDestroyOnLoad)

→ Loads:

[GameScene] + [HUDScene] (Additive)

→ Player finishes level → Load:

[ScoreScene]
```

### Summary
Unity Scenes are:
* Modular containers for game content and logic
* Essential for managing states and transitions
* Editable in the Unity Editor
* Loadable via script at runtime (single or additive)

They are a critical building block for any Unity-based game or application.

