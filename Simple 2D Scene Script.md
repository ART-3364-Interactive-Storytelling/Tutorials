# Detailed Description of the Simple 2D Scene Script

The script we wrote for the Simple 2D Scene Script is below:

<img width="663" height="384" alt="Screenshot 2025-08-06 at 3 37 38 PM" src="https://github.com/user-attachments/assets/add55305-327d-49db-bf38-fcb2d858627d" />


| Line  | Description   |
| ------| ------------- |
|   1   | The ```using``` directive imports namespaces into your code file. This means you can refer to types within that namespace directly by their names without needing to specify their fully qualified names.  Without this line we would have to reference objects and functions by their fully qualified name. We'd have to use ```UnityEngine.MonoBehaviour``` instead of ```MonoBehaviour``` |
|   3   | We declare a class called ```PlayerMovement``` the derives / inherits from ```MonoBehaviour```[^1]. We also say ```PlayerMovement``` derives ```MonoBehaviour```  |
|   5   | We declare a variable of type ***float*** named ```moveSpeed``` and give it an initial value of 5.0.  Because we declare it ```public``` we can access it from outside of our ```PlayerMovement``` class. |
|   7   | Here override the function ```Update``` to make it specialized for our ```PlayerMovement``` class.  If we didn't override it we would use the version of ```Update``` that we inherit fro our parent class |
|   9   | We declare a local variable ```moveX``` of type ```float``` and we assign it the value returned by the function ```Input.GetAxis ("Horizontal");``` Notice we are using the class ```Input``` provided by the ```UnityEngine```.  We are calling the ```GetAxis``` function from the ```Input``` class and asking it to return the current horizontal value. You can find additional information on the ```GetAxis``` function in the Unity [Documentation](https://docs.unity3d.com/ScriptReference/Input.GetAxis.html).|
|  10   | We declare a local variable ```moveY``` of type ```float``` and we assign it the value returned by the function ```Input.GetAxis ("Vertical");``` Notice we are using the class ```Input``` provided by the ```UnityEngine```. |
|  12   | We declare a new local variable of type ```Vector3``` and call it ```move```.  We use the keyword ```new``` to allocate a new object.  When you call ```new``` you have to call the constructor of the object.  ```Vector3(moveX, movey, 0)``` is the constructor for the ```Vector3``` class.  The ```Vector3``` class represents a three dimensional [vector](https://en.wikipedia.org/wiki/Vector_(mathematics_and_physics)). Vectors can represent any three-dimensional type, perhaps velocity in the x-rotation, y-rotation, or z-rotation. In this case we're using the three-dimensional vector to represent a three-dimensional velocity in space.  We set the x  And we're making a 2D game so we set the Z value to 0.|
|  13   | Now we take the ```transform``` component of our ```PlayerMovement``` and increment it by out ```move``` vector times our ```moveSpeed``` times ```Time.deltaTime```[^2] |

[^1]: Why does Unity use the British spelling?  It was originally developed by a Danish company.  As a result a lot of British-isms and American-isms.  It gives coding in Unity a little colour, or color.

[^2]: ```Time.deltaTime``` gives you the time in seconds that passed since the last frame — also known as the frame delta. If we didn't use the frame delta out game would run at different speeds for people with different video cards.  By using delta time we ensure velocity and movement stays smooth on a nvidia 5080 and a 1080.
