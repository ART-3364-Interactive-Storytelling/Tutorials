# C# Program Structure
=====================================

## Introduction
---------------

C# is a modern, object-oriented programming language developed by Microsoft as a part of its .NET initiative. A C# program consists of a series of statements that are executed in sequence. 

## Namespace
------------

A C# program typically begins with a `namespace` declaration. Namespaces are used to organize related classes, interfaces, and other types.

```csharp
namespace MyProgram
{
    // Program code here
}
```

## Class
---------

A C# program must contain at least one `class` declaration. The `class` declaration is used to define a new class.

```csharp
namespace MyProgram
{
    public class MyClass
    {
        // Class members here
    }
}
```

## Main Method
--------------

The `Main` method is the entry point of a C# program. It is the method that is called when the program starts.

```csharp
namespace MyProgram
{
    public class MyClass
    {
        public static void Main(string[] args)
        {
            // Program code here
        }
    }
}
```

## Variables and Data Types
---------------------------

C# is a statically-typed language, which means that the data type of a variable must be known at compile time. C# supports a variety of data types, including:

*   Integers (`int`)
*   Floating-point numbers (`float`, `double`, `decimal`)
*   Characters (`char`)
*   Boolean values (`bool`)
*   Strings (`string`)

```csharp
int myInteger = 10;
float myFloat = 10.5f;
double myDouble = 10.5;
decimal myDecimal = 10.5m;
char myChar = 'a';
bool myBool = true;
string myString = "Hello, World!";
```

## Operators
------------

C# supports a variety of operators, including:

*   Arithmetic operators (`+`, `-`, `*`, `/`, `%`, etc.)
*   Comparison operators (`==`, `!=`, `>`, `<`, `>=` , `<=`)
*   Logical operators (`&&`, `||`, `!`)
*   Assignment operators (`=`, `+=`, `-=`, `*=`, `/=`, etc.)

```csharp
int x = 10;
int y = 5;

int sum = x + y;
int difference = x - y;
int product = x * y;
int quotient = x / y;
```

## Control Flow
----------------

C# supports a variety of control flow statements, including:

*   Conditional statements (`if`, `else`, `switch`)
*   Loops (`for`, `while`, `do-while`)
*   Jump statements (`break`, `continue`, `return`, `throw`)

```csharp
if (x > y)
{
    Console.WriteLine("x is greater than y");
}
else
{
    Console.WriteLine("x is less than or equal to y");
}

for (int i = 0; i < 10; i++)
{
    Console.WriteLine(i);
}

while (x > 0)
{
    Console.WriteLine(x);
    x--;
}

do
{
    Console.WriteLine(x);
    x--;
} while (x > 0);
```

## Functions
-------------

C# supports functions, which are blocks of code that can be called multiple times from different parts of a program.

```csharp
public static void MyFunction()
{
    Console.WriteLine("Hello, World!");
}

public static void Main(string[] args)
{
    MyFunction();
}
```

Here is an example of a simple C# program that demonstrates some of the concepts covered in this document:

```csharp
using System;

namespace MyProgram
{
    public class MyClass
    {
        public static void Main(string[] args)
        {
            int x = 10;
            int y = 5;

            if (x > y)
            {
                Console.WriteLine("x is greater than y");
            }
            else
            {
                Console.WriteLine("x is less than or equal to y");
            }

            for (int i = 0; i < 10; i++)
            {
                Console.WriteLine(i);
            }

            MyFunction();
        }

        public static void MyFunction()
        {
            Console.WriteLine("Hello, World!");
        }
    }
}
```

This program declares a namespace, a class, and a `Main` method. It also demonstrates the use of variables, conditional statements, loops, and functions.
