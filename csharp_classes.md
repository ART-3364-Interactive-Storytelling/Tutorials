# C# Classes
## Overview
In C#, a class is a blueprint for creating objects that contain data and functions that operate on that data. Classes are a fundamental concept in object-oriented programming (OOP) and are used to define custom data types.  You can think you a class as a collection of related data and functions or methods that act upon that data.

## Class Structure
A basic class in C# consists of the following elements:
```csharp
public class ClassName 
{
    // Fields
    private type fieldName;

    // Properties
    public type PropertyName 
    { 
        get { return fieldName; } 
        set { fieldName = value; } 
    }

    // Constructors
    public ClassName() 
    { 
        // Initialization code
    }

    // Methods
    public return-type MethodName(parameters) 
    { 
        // Method implementation
    }
}
```
## Class Components

*   **Fields**: These are the data members of the class, which are used to store the state of an object. Fields can be private, public, protected, or internal, depending on the access modifier used.
*   **Properties**: Properties are used to expose the fields of a class in a controlled manner. They provide a way to get and set the values of fields, while also allowing for validation and other logic to be applied.
*   **Constructors**: Constructors are special methods that are used to initialize objects when they are created. They have the same name as the class and do not have a return type, not even `void`.
*   **Methods**: Methods are functions that belong to a class and are used to perform operations on objects. They can take parameters, return values, and can be overloaded to provide multiple implementations with different parameter lists.

## Access Modifiers in C#
Access modifiers are used to control the accessibility of classes, methods, properties, and fields in C#. They determine the level of access that other parts of the program have to these members.

### Public
*   **Definition**: The `public` access modifier makes a member accessible from any part of the program.
*   **Description**: When a member is declared as `public`, it can be accessed from any class, regardless of whether it's in the same [assembly](CSharp_Assembly.md)[^1] or not.
*   **Example**:
```csharp
public class MyClass 
{
    public void MyMethod() 
    {
        // Code here
    }
}
```
In this example, `MyMethod` can be called from any class in the program.

### Private
*   **Definition**: The `private` access modifier makes a member accessible only within the same class.
*   **Description**: When a member is declared as `private`, it can only be accessed within the class where it's declared. This means that other classes, even if they're in the same [assembly](CSharp_Assembly.md), cannot access the member directly.
*   **Example**:
```csharp
public class MyClass 
{
    private void MyMethod() 
    {
        // Code here
    }

    public void AnotherMethod() 
    {
        MyMethod(); // This is allowed
    }
}
```
In this example, `MyMethod` can only be called from within `MyClass`.

### Protected
*   **Definition**: The `protected` access modifier makes a member accessible within the same class and within any class that inherits from that class.
*   **Description**: When a member is declared as `protected`, it can be accessed within the class where it's declared, as well as within any classes that inherit from that class.
*   **Example**:
```csharp
public class MyBaseClass 
{
    protected void MyMethod() 
    {
        // Code here
    }
}

public class MyDerivedClass : MyBaseClass 
{
    public void AnotherMethod() 
    {
        MyMethod(); // This is allowed
    }
}
```
In this example, `MyMethod` can be called from within `MyBaseClass` and `MyDerivedClass`.

### Internal
*   **Definition**: The `internal` access modifier makes a member accessible only within the same [assembly](CSharp_Assembly.md).
*   **Description**: When a member is declared as `internal`, it can be accessed from any class within the same [assembly](CSharp_Assembly.md), but not from classes in other assemblies.
*   **Example**:
```csharp
internal class MyClass 
{
    internal void MyMethod() 
    {
        // Code here
    }
}
```
In this example, `MyClass` and `MyMethod` can only be accessed from within the same [assembly](CSharp_Assembly.md).

### Comparison of Access Modifiers
| Access Modifier | Same Class | Same Assembly | Different Assembly | Inherited Classes |
| --- | --- | --- | --- | --- |
| `public` | Yes | Yes | Yes | Yes |
| `private` | Yes | No | No | No |
| `protected` | Yes | Yes | No | Yes |
| `internal` | Yes | Yes | No | Yes (if inherited within same [assembly](CSharp_Assembly.md)) |

Note that the `internal` access modifier can be combined with `protected` to create `protected internal`, which allows access from the same [assembly](CSharp_Assembly.md) and from inherited classes in the same [assembly](CSharp_Assembly.md).

## Example Class
Here's an example of a simple `Person` class in C#:
```csharp
public class Person 
{
    private string name;
    private int age;

    public Person(string name, int age) 
    {
        this.name = name;
        this.age = age;
    }

    public string Name 
    { 
        get { return name; } 
        set { name = value; } 
    }

    public int Age 
    { 
        get { return age; } 
        set { age = value; } 
    }

    public void SayHello() 
    {
        Console.WriteLine($"Hello, my name is {name} and I am {age} years old.");
    }
}
```

This `Person` class has two fields (`name` and `age`), a constructor to initialize objects, properties to expose the fields, and a method (`SayHello`) to perform an action.

## Using the Class
To use the `Person` class, you can create objects and call methods like this:
```csharp
class Program 
{
    static void Main() 
    {
        Person person = new Person("John Doe", 30);
        person.SayHello();
    }
}
```
This code creates a new `Person` object named `person` and calls the `SayHello` method to print a greeting message to the console.

[^1]: An [assembly](CSharp_Assembly.md) in C# is a compiled collection of code, data, and metadata that forms a single unit of deployment and reuse. Assemblies are the building blocks of .NET applications and can contain one or more files, such as DLLs (dynamic-link libraries) or EXEs (executables).  Assemblies can be thought of as containers that hold the compiled code, resources, and metadata for a .NET application. They provide a way to package

