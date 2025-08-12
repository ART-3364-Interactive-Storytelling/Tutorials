# C# Data Types
================

C# is a statically-typed language, which means that the data type of a variable must be known at compile time. Below, are the different data types available in C#.

## Value Types
-------------

Value types are types that store their values directly in memory. They are divided into several categories:

### Integer Types

*   `byte`: An 8-bit unsigned integer, ranging from 0 to 255.
*   `sbyte`: An 8-bit signed integer, ranging from -128 to 127.
*   `short`: A 16-bit signed integer, ranging from -32,768 to 32,767.
*   `ushort`: A 16-bit unsigned integer, ranging from 0 to 65,535.
*   `int`: A 32-bit signed integer, ranging from -2,147,483,648 to 2,147,483,647.
*   `uint`: A 32-bit unsigned integer, ranging from 0 to 4,294,967,295.
*   `long`: A 64-bit signed integer, ranging from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.
*   `ulong`: A 64-bit unsigned integer, ranging from 0 to 18,446,744,073,709,551,615.

```csharp
byte myByte = 10;
sbyte mySByte = -10;
short myShort = 10;
ushort myUShort = 10;
int myInt = 10;
uint myUInt = 10;
long myLong = 10;
ulong myULong = 10;
```

### Floating-Point Types

*   `float`: A 32-bit floating-point number, with a precision of about 7 decimal digits.
*   `double`: A 64-bit floating-point number, with a precision of about 15 decimal digits.
*   `decimal`: A 128-bit decimal number, with a precision of 28-29 decimal digits.

```csharp
float myFloat = 10.5f;
double myDouble = 10.5;
decimal myDecimal = 10.5m;
```

### Boolean Type

*   `bool`: A boolean value, which can be either `true` or `false`.

```csharp
bool myBool = true;
```

### Character Type

*   `char`: A 16-bit Unicode character.

```csharp
char myChar = 'a';
```

## Reference Types
-----------------

Reference types are types that store a reference to a value in memory. They are divided into several categories:

### String Type

*   `string`: A sequence of characters.

```csharp
string myString = "Hello, World!";
```

### Array Type

*   `array`: A collection of values of the same type.

```csharp
int[] myArray = new int[] { 1, 2, 3, 4, 5 };
```

### Class Type

*   `class`: A custom reference type defined using the `class` keyword.

```csharp
public class MyClass
{
    public int MyProperty { get; set; }
}

MyClass myClass = new MyClass();
```

### Interface Type

*   `interface`: A custom reference type defined using the `interface` keyword.

```csharp
public interface MyInterface
{
    void MyMethod();
}

public class MyClass : MyInterface
{
    public void MyMethod()
    {
        Console.WriteLine("Hello, World!");
    }
}

MyInterface myInterface = new MyClass();
```

### Delegate Type

*   `delegate`: A type that represents a reference to a method with a specific signature.

```csharp
public delegate void MyDelegate();

public class MyClass
{
    public void MyMethod()
    {
        Console.WriteLine("Hello, World!");
    }
}

MyClass myClass = new MyClass();
MyDelegate myDelegate = new MyDelegate(myClass.MyMethod);
myDelegate();
```

### Nullable Reference Types

*   `?`: A nullable reference type, which can be used to represent a reference type that can be null.

```csharp
string? myString = null;
```

## Enum Type
------------

*   `enum`: A value type that represents a set of named constants.

```csharp
public enum MyEnum
{
    Value1,
    Value2,
    Value3
}

MyEnum myEnum = MyEnum.Value1;
```

## Tuple Type
-------------

*   `tuple`: A value type that represents a set of values.

```csharp
var myTuple = (1, 2, 3);
```

## Record Type
--------------

*   `record`: A reference type that represents a set of values.

```csharp
public record MyRecord(int X, int Y);

MyRecord myRecord = new MyRecord(1, 2);
```

## Example Use Case

Here is an example of a simple C# program that demonstrates some of the data types covered in this document:

```csharp
using System;

public class MyClass
{
    public int MyProperty { get; set; }

    public MyClass(int myProperty)
    {
        MyProperty = myProperty;
    }
}

public enum MyEnum
{
    Value1,
    Value2,
    Value3
}

public record MyRecord(int X, int Y);

class Program
{
    static void Main(string[] args)
    {
        int myInt = 10;
        float myFloat = 10.5f;
        double myDouble = 10.5;
        decimal myDecimal = 10.5m;
        bool myBool = true;
        char myChar = 'a';
        string myString = "Hello, World!";
        int[] myArray = new int[] { 1, 2, 3, 4, 5 };
        MyClass myClass = new MyClass(10);
        MyEnum myEnum = MyEnum.Value1;
        var myTuple = (1, 2, 3);
        MyRecord myRecord = new MyRecord(1, 2);

        Console.WriteLine(myInt);
        Console.WriteLine(myFloat);
        Console.WriteLine(myDouble);
        Console.WriteLine(myDecimal);
        Console.WriteLine(myBool);
        Console.WriteLine(myChar);
        Console.WriteLine(myString);
        Console.WriteLine(string.Join(", ", myArray));
        Console.WriteLine(myClass.MyProperty);
        Console.WriteLine(myEnum);
        Console.WriteLine(myTuple);
        Console.WriteLine(myRecord);
    }
}
```

This program demonstrates the use of various data types, including integer types, floating-point types, boolean type, character type, string type, array type, class type, enum type, tuple type, and record type.
