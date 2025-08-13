# DontDestroyOnLoad and Scenes in Unity

## Introduction

In Unity, scenes are used to organize and structure your game or application. However, when switching between scenes, Unity will unload the current scene and load the new one, which can cause issues with objects that need to persist across scenes. This is where `DontDestroyOnLoad` comes in - a method that allows you to preserve objects across scene loads.

## What is DontDestroyOnLoad?

`DontDestroyOnLoad` is a method in Unity that prevents an object from being destroyed when a scene is unloaded. This means that the object will remain in memory and will not be garbage collected, even when the scene is unloaded.

## When to Use DontDestroyOnLoad

You should use `DontDestroyOnLoad` when you need to preserve an object across scene loads. Here are some examples of when you might want to use `DontDestroyOnLoad`:

* **Music and sound effects**: If you have a music player or sound effects that need to continue playing across scenes, you can use `DontDestroyOnLoad` to preserve the object.
* **Game managers**: If you have a game manager that needs to keep track of game state across scenes, you can use `DontDestroyOnLoad` to preserve the object.
* **UI elements**: If you have UI elements that need to be preserved across scenes, such as a score display or a health bar, you can use `DontDestroyOnLoad` to preserve the object.

## How to Use DontDestroyOnLoad

To use `DontDestroyOnLoad`, you need to call the method on the object you want to preserve. Here is an example:
```csharp
using UnityEngine;

public class MusicPlayer : MonoBehaviour
{
    private void Awake()
    {
        DontDestroyOnLoad(gameObject);
    }
}
```
In this example, the `MusicPlayer` object is preserved across scene loads by calling `DontDestroyOnLoad` in the `Awake` method.

## Best Practices for Using DontDestroyOnLoad

Here are some best practices to keep in mind when using `DontDestroyOnLoad`:

* **Use it sparingly**: Only use `DontDestroyOnLoad` when necessary, as it can cause memory leaks if not used carefully.
* **Use it in Awake**: Call `DontDestroyOnLoad` in the `Awake` method, as this is the earliest point in the object's lifecycle where it can be called.
* **Use it on the root object**: Call `DontDestroyOnLoad` on the root object of the hierarchy, as this will preserve all child objects as well.

## Scene Management with DontDestroyOnLoad

When using `DontDestroyOnLoad`, you need to be careful when managing scenes. Here are some tips:

* **Use SceneManager.LoadScene**: Use `SceneManager.LoadScene` to load new scenes, as this will allow you to preserve objects across scene loads.
* **Use SceneManager.UnloadScene**: Use `SceneManager.UnloadScene` to unload scenes, as this will allow you to remove unnecessary scenes from memory.
* **Use SceneManager.LoadSceneMode.Additive**: Use `SceneManager.LoadSceneMode.Additive` to load new scenes additively, which will allow you to preserve objects across scene loads.

## Example Use Case

Here is an example use case for `DontDestroyOnLoad`:
```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

public class GameManager : MonoBehaviour
{
    private void Awake()
    {
        DontDestroyOnLoad(gameObject);
    }

    public void LoadNextScene()
    {
        SceneManager.LoadScene("NextScene");
    }
}
```
In this example, the `GameManager` object is preserved across scene loads using `DontDestroyOnLoad`. The `LoadNextScene` method is used to load the next scene, which will preserve the `GameManager` object.

### Further Reading

For more information on `DontDestroyOnLoad` and scene management in Unity, check out the following resources:

* [Unity Documentation: DontDestroyOnLoad](https://docs.unity3d.com/ScriptReference/Object.DontDestroyOnLoad.html)
* [Unity Documentation: SceneManager](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.html)
* [Unity Tutorial: Scene Management](https://unity3d.com/learn/tutorials/topics/interface-essentials/scene-management)
