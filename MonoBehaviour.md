# MonoBehaviour in Unity

`MonoBehaviour` is the **base class** from which every Unity script derives (unless it's a special data structure like `ScriptableObject`). It provides Unity-specific functionality, including:

- Access to GameObject lifecycle events
- Communication with the Unity engine (e.g., coroutines, collision events)
- Integration into the Unity Editor and Play Mode

```csharp
using UnityEngine;

public class MyScript : MonoBehaviour
{
    void Start() {
        Debug.Log("Hello from Start!");
    }

    void Update() {
        Debug.Log("Running every frame.");
    }
}
```
When this script is attached to a GameObject, Unity will automatically call the relevant methods at the correct times.

## Purpose of MonoBehaviour
| Feature | Description
|------------------|-------------|
| Lifecycle Management | Enables Unity to call methods like ```Start()```, ```Update()```, ```OnDestroy()```, etc.
| Event Handling | Detects collisions, triggers, input, mouse events, etc.
| Coroutine Support | Enables asynchronous behaviors using ```StartCoroutine()```
| Editor Integration | Scripts appear in the Inspector when attached to GameObjects
| Communication with Engine | Access Unity APIs for physics, rendering, input, etc.

## Lifecycle Methods

Unity invokes a specific set of methods on MonoBehaviour components during different stages of runtime.

### Initialization Methods

| Method | Called When
|------------------|-------------|
| ```Awake()```| Once, when the script instance is loaded
| ```OnEnable()```| Every time the script becomes enabled
| ```Start()```| Before the first ```Update()``` call, if the script is enabled

### Frame Update Methods

| Method | Description
|------------------|-------------|
| ```Update()```| Called once per frame
| ```LateUpdate()```| Called after all ```Update()``` calls
| ```FixedUpdate()```| Called at fixed time intervals (used for physics)

### Physics Callbacks

| Method | Description
|------------------|-------------|
| ```OnCollisionEnter2D()```| Called when a 2D collider hits another
| ```OnTriggerEnter2D()```| Called when a 2D trigger overlaps another
| ```OnCollisionExit()```, etc. | Variants for start/end of collision

### Disable/Destroy Methods

| Method| Description
|------------------|-------------|
| ```OnDisable()```| Called when the script is disabled
| ```OnDestroy()```| Called before the object is destroyed

###  Execution Order

The lifecycle method order for an active GameObject:
```
Awake()
OnEnable()
Start()
Update() ← every frame
OnDisable()
OnDestroy()
```
You can manually control script execution order in **Edit → Project Settings → Script Execution Order.**

 ### Important Rules
* You cannot use constructors (new) to create MonoBehaviours.
*	Use ```AddComponent<T>()``` to attach a MonoBehaviour to a GameObject.
* MonoBehaviours must be attached to a GameObject to receive lifecycle calls.
* Disabling the GameObject or component disables all callbacks like ```Update()```.

⸻

### Common Use Cases

| Use Case | MonoBehaviour Role
|------------------|-------------|
| Player movement | ```Update()``` for input, ```FixedUpdate()``` for physics
| Enemy AI | State updates in ```Update()```
| Animation control | Triggering transitions from ```Update()``` or Coroutines
| UI interaction | Respond to mouse or keyboard input
| Scene loading | ```Start()``` to load data or setup objects
| Sound triggers | ```OnTriggerEnter()``` to play audio

### Best Practices
* Avoid heavy logic in Update(); optimize with event-based design when possible.
* Use ```Awake()``` for internal setup, ```Start()``` for interactions with other objects.
* Only start coroutines when needed, and always ```StopCoroutine()``` if required.
* Avoid tightly coupling MonoBehaviour components — prefer composition and messaging.
* Group behavior in logical scripts (e.g., PlayerController, HealthSystem).
