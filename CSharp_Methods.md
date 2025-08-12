# C# Methods
================

C# methods are blocks of code that can be called multiple times from different parts of a program. They are used to perform specific tasks and can be reused throughout a program. 

## Method Declaration
-------------------

A C# method is declared using the following syntax:

```csharp
[modifiers] return-type method-name([parameters])
{
    // method body
}
```

*   `[modifiers]`: Optional modifiers such as `public`, `private`, `static`, etc.
*   `return-type`: The data type of the value returned by the method.
*   `method-name`: The name of the method.
*   `[parameters]`: Optional parameters that are passed to the method.

## Return Types
----------------

A C# method can return a value of any data type, including `void`, which means the method does not return any value.

```csharp
public int Add(int x, int y)
{
    return x + y;
}

public void PrintHello()
{
    Console.WriteLine("Hello");
}
```

## Parameters
--------------

A C# method can take zero or more parameters, which are values passed to the method when it is called.

```csharp
public int Add(int x, int y)
{
    return x + y;
}

public void PrintHello(string name)
{
    Console.WriteLine($"Hello, {name}!");
}
```

### Parameter Modifiers

C# provides several parameter modifiers that can be used to modify the behavior of parameters:

*   `out`: The parameter is passed by reference and must be assigned a value before the method returns.
*   `ref`: The parameter is passed by reference and can be modified by the method.
*   `in`: The parameter is passed by reference and cannot be modified by the method.
*   `params`: The parameter is an array of values that can be passed to the method.

```csharp
public void Add(int x, int y, out int result)
{
    result = x + y;
}

public void PrintHello(ref string name)
{
    name = "John";
    Console.WriteLine($"Hello, {name}!");
}

public void PrintHello(in string name)
{
    Console.WriteLine($"Hello, {name}!");
}

public void PrintHello(params string[] names)
{
    foreach (var name in names)
    {
        Console.WriteLine($"Hello, {name}!");
    }
}
```

## Method Modifiers
-------------------

C# provides several method modifiers that can be used to modify the behavior of methods:

*   `public`: The method can be accessed from any part of the program.
*   `private`: The method can only be accessed within the same class.
*   `protected`: The method can be accessed within the same class and any derived classes.
*   `internal`: The method can be accessed within the same assembly.
*   `static`: The method belongs to the class itself and can be called without creating an instance of the class.
*   `const`: The method is a constant and cannot be modified.
*   `new`: The method hides a method with the same name in a base class.
*   `override`: The method overrides a method with the same name in a base class.
*   `abstract`: The method is declared but not implemented and must be implemented by any derived classes.
*   `sealed`: The method cannot be overridden by any derived classes.
*   `virtual`: The method can be overridden by any derived classes.

```csharp
public class MyClass
{
    public void PrintHello()
    {
        Console.WriteLine("Hello");
    }

    private void PrintGoodbye()
    {
        Console.WriteLine("Goodbye");
    }

    protected void PrintWelcome()
    {
        Console.WriteLine("Welcome");
    }

    internal void PrintThanks()
    {
        Console.WriteLine("Thanks");
    }

    public static void PrintHelloStatic()
    {
        Console.WriteLine("Hello Static");
    }

    public const int MyConstant = 10;

    public new void PrintHelloNew()
    {
        Console.WriteLine("Hello New");
    }

    public override void PrintHelloOverride()
    {
        Console.WriteLine("Hello Override");
    }

    public abstract void PrintHelloAbstract();

    public sealed void PrintHelloSealed()
    {
        Console.WriteLine("Hello Sealed");
    }

    public virtual void PrintHelloVirtual()
    {
        Console.WriteLine("Hello Virtual");
    }
}
```

## Method Overloading
---------------------

C# allows method overloading, which means multiple methods with the same name can be declared as long as they have different parameter lists.

```csharp
public class MyClass
{
    public void PrintHello()
    {
        Console.WriteLine("Hello");
    }

    public void PrintHello(string name)
    {
        Console.WriteLine($"Hello, {name}!");
    }

    public void PrintHello(int age)
    {
        Console.WriteLine($"Hello, you are {age} years old!");
    }
}
```

## Method Hiding
----------------

C# allows method hiding, which means a method in a derived class can hide a method with the same name in a base class using the `new` keyword.

```csharp
public class MyBaseClass
{
    public void PrintHello()
    {
        Console.WriteLine("Hello");
    }
}

public class MyDerivedClass : MyBaseClass
{
    public new void PrintHello()
    {
        Console.WriteLine("Hello New");
    }
}
```

## Method Overriding
--------------------

C# allows method overriding, which means a method in a derived class can override a method with the same name in a base class using the `override` keyword.

```csharp
public class MyBaseClass
{
    public virtual void PrintHello()
    {
        Console.WriteLine("Hello");
    }
}

public class MyDerivedClass : MyBaseClass
{
    public override void PrintHello()
    {
        Console.WriteLine("Hello Override");
    }
}
```

## Example Use Case

Here is an example of a simple C# program that demonstrates some of the concepts covered in this document:

```csharp
using System;

public class MyClass
{
    public void PrintHello()
    {
        Console.WriteLine("Hello");
    }

    public void PrintHello(string name)
    {
        Console.WriteLine($"Hello, {name}!");
    }

    public void PrintHello(int age)
    {
        Console.WriteLine($"Hello, you are {age} years old!");
    }

    public static void PrintHelloStatic()
    {
        Console.WriteLine("Hello Static");
    }

    public const int MyConstant = 10;

    public new void PrintHelloNew()
    {
        Console.WriteLine("Hello New");
    }

    public override void PrintHelloOverride()
    {
        Console.WriteLine("Hello Override");
    }

    public abstract void PrintHelloAbstract();

    public sealed void PrintHelloSealed()
    {
        Console.WriteLine("Hello Sealed");
    }

    public virtual void PrintHelloVirtual()
    {
        Console.WriteLine("Hello Virtual");
    }
}

class Program
{
    static void Main(string[] args)
    {
        MyClass myClass = new MyClass();
        myClass.PrintHello();
        myClass.PrintHello("John");
        myClass.PrintHello(30);
        MyClass.PrintHelloStatic();
        myClass.PrintHelloNew();
        myClass.PrintHelloOverride();
        myClass.PrintHelloSealed();
        myClass.PrintHelloVirtual();
    }
}
```

This program demonstrates the use of various method modifiers, method overloading, method hiding, and method overriding.
