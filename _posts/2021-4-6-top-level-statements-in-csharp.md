---
layout: post
title: Top Level Statements
tags: c-sharp
---

C# 9.0 introduced top-level statements that allow you to skip all the boilerplate code and get to the point quickly. No need to declare a namespace, class, or even a `Main()` method. Just open your editor and start writing beautiful C# code. 

Writing a simple console program in C# has always involved a ton of ceremony. You have to create a class named Program. Then declare the `Main` method that is `public`, `static`, `void`, and takes an array of strings as arguments. Here is an example. 

```c#
using System;

class Program
{
    static void Main(string[] args)
    {
        int sum = 45 + 50;
        Console.WriteLine(sum);
    }
}
```

In the above example, there is too much clutter. There are only two lines that are actually doing something. When a beginner reads the above program, it can feel quite overwhelming. 

- What is System? Why are we **using** it?
- What is a class? Where are the students?
- What is static, why is it void? 
- What is args?

The essential part in the above program is the code that adds and displays the sum of two numbers. Rest is just ceremony. 

In C# 9.0, you can simply write this:

```c#
int sum = 45 + 50;
System.Console.WriteLine(sum);
```

Using [sharplab,](https://sharplab.io/#v2:CYLg1APglgdgLgAgM4FcC2CC8CAsBWBMBPABgG4BYAKAAEBGAOnoE4AKVNASjKA=) we can see how the C# compiler transforms this code before it's compiled. Notice that the `Program` class and `Main` method are still getting generated behind the scenes, but you don't have to write them. 

```c#
using System;
using System.Diagnostics;
using System.Reflection;
using System.Runtime.CompilerServices;
using System.Security;
using System.Security.Permissions;

[CompilerGenerated]
internal static class <Program>$
{
    private static void <Main>$(string[] args)
    {
        int value = 95;
        Console.WriteLine(value);
    }
}
```

**What happens to the command-line arguments?**

They are still accessible using the `args` array. You can run the following code using `dotnet run hello`, and it will print **hello** to the console.

```c#
System.Console.WriteLine(args[0]);
```

**How can I return a status code?**

Just return it, as you normally would. For example, 

```c#
System.Console.WriteLine("Hello");
return 0;
```

**Can I have multiple files with top-level statements?**

No. Only one file in your application can use top-level statements. The compiler throws an error when it finds multiple files containing top-level statements. 

**Can I create classes in the same file?**

Yes, the only requirement is that the top-level statements should come before any type declaration. For example, 

```c#
using System;

var animal = new Animal { Name = "Dog" };
Console.WriteLine(animal.Name);

class Animal
{
    public string Name { get; set; }
}
```

You can't create a class and then write your statements. For example, this code is invalid. 

```c#
using System;

class Animal
{
    public string Name { get; set; }
}

var animal = new Animal { Name = "Dog" };
Console.WriteLine(animal.Name);
```

It throws the following error. 

```c#
error CS8803: Top-level statements must precede namespace and type declarations. 
```

Top-level statements make C# beginner-friendly, giving it a scripty feel, like Ruby or Python. They also make simple programs clear and expressive. If you just want to understand a concept in C# or try out a base class library, you can quickly do so using the top-level statements. They are also great for small tools and utilities. 

Did I miss anything? Let me know. 

