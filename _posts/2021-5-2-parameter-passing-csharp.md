---
layout: post
title: Parameter Passing in C#
tags: c-sharp
---

This article is a deep dive into parameter passing in C#. It shows how we always pass the variables by value. It also explains the **ref**, **out**, and **in** parameter modifiers which give us control over parameter passing.

In C#, most of the methods can have zero or more parameters that define the data provided to the method. Any code that calls the method has to pass the data, also known as arguments. Consider the following method and subsequent method call.

```csharp
static void Greet(string greeting)
{
   Console.WriteLine(greeting);
}
...
Greet("Hello");
```

In the above example, greeting is a parameter of the `Greet()` method, and `Hello` is an argument passed to the method. 

When you call a method and pass arguments, they are passed by value, which means a copy of the value is created when passed to the method. Any changes made to the argument inside the method are not reflected on the original variable. 

```c#
using System;

int number = 8;

Increase(number);

Console.WriteLine(number);  // prints 8

static void Increase(int num)
{
   num = num + 1;

   Console.WriteLine(num);   // prints 9
}
```

When you pass a reference type variable, such as an object, C# still copies the reference by value, because the variable holds the reference, not the actual object. So even though a copy of the reference variable is passed around, both of them refer to the same object in the memory. So any changes made to the object by the variable inside the method are visible to the variable outside the method. 

```csharp
using System;

var john = new User
{
   Name = "John",
   Salary = 50000
};

Promote(john);
Console.WriteLine(john.Salary);     // prints 60000

static void Promote(User u)
{
   u.Salary += 10000;
   Console.WriteLine(u.Salary);    // prints 60000
}
```

However, if you change the variable’s value itself inside the method, that change is not reflected outside the method, as only a copy was changed, not the actual object. For example, we can assign the argument to null inside the method, and the actual variable will remain unchanged. 

```csharp
using System;

var john = new User
{
   Name = "John",
   Salary = 50000
};

Promote(john);
Console.WriteLine(john.Salary);     // prints 50000

static void Promote(User u)
{
   u = null;
}
```

C# allows three different modifier keywords using which you can control the parameters of methods. 

**The `ref` modifier**

C# allows you to pass parameters by reference using the `ref` modifier. It doesn’t matter if the variable getting passed belongs to a reference type or a value type. Both the parameter and the argument will refer to the same memory location. 

In the following example, setting the argument `u` to null will also make the variable `john` null, causing the null reference exception. 

```csharp
using System;

var john = new User
{
   Name = "John",
   Salary = 50000
};

Promote(ref john);
Console.WriteLine(john.Salary);     // throws System.NullReferenceException

static void Promote(ref User u)
{
   u = null;
}
```

You should initialize an argument passed with a `ref` modifier before it is passed to the method. 

**The `out` modifier**

It is similar to the `ref` modifier, except

- You don't have to initialize the argument before before passing it to the method.
- The method must initialize the argument before it comes out of the function. 

In the example below, the `Hire` function initializes a new user object passed to it via the out modifier. Notice that the variable is variable `john` is declared on the fly when calling the Hire method. 

```csharp
using System;

Hire(out User john);

Console.WriteLine(john.Salary);     // prints 50000

static void Hire(out User u)
{
   u = new User
   {
       Name = "John",
       Salary = 50000
   };
}
```

Like the `ref` modifier, a variable marked by the `out` modifier is passed by reference. 

Often an `out` variable is used to get multiple return values from a function as follows:

```csharp
using System;

var john = new User
{
   Name = "John",
   Salary = 50000
};

bool shouldPromote = Raise(john.Salary, out double hike);

Console.WriteLine(shouldPromote);   // True
Console.WriteLine($"Hike Amount = {hike}");     // prints 5000

static bool Raise(int salary, out double hike)
{
   hike = salary * 0.1;
   return hike < 7000;
}
```

**The `in` modifier**

It is similar to the `ref` and `out` parameters, except that the method accepting a in argument’s value cannot modify the argument. If it tries, the C# compiler generates a compile-time error. 

The `in` parameter saves the compiler from copying a large value type’s memory to the parameter variable while preventing the object from accidental modification. This makes it very useful when passing a large value type to the method. 

```csharp
var point = new Coord();
Verify(point);

static void Verify(in Coord c)
{
  // error: Cannot assign to variable 'in Coord' because it is a readonly variable
   c = new Coord(); 
}

struct Coord
{
   public int X;

   public int Y;
}
```

