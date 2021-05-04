---
layout: post
title: Generics in C#
tags: c-sharp
---

Generics were added in version 2.0 of C# and are among the most important concepts in the language. They enable you to write reusable, high-performance code that is type-safe at compile time. Using generics, you can use a type in your code without knowing about it beforehand. This article provides an introduction to generics. 

Generics are used in many places in .NET, including collections, delegates, and asynchronous code. With generics, you don't need to know the size of the collection beforehand, and you can use generics with any element type, even the custom data types specific to your code. C# provides support for both generic types (classes, interfaces, etc.) and generic methods. 

In generics, you have type parameters and type arguments. This is similar to a method that has parameters, and you pass arguments to the method. 

### Generic Types

The syntax to declare a generic type consists of type parameters in angle brackets after the name of the type. For example, Locator<T> is a generic class in the example below. 

```csharp
public class Locator<T>
{
    
}
```

To create an instance of Locator<T>, you use the new keyword, followed by the name of the class. However, instead of T, you specify the actual type you want to pass as an argument. The following example passes string type as an argument. 

```c#
var stringLocator = new Locator<string>();
```

You can use the type parameter (T) on the class methods, as shown in the example below. 

```csharp
public class Locator<T>
{
    public IList<T> Items { get; set; }

    public T Locate(int index) 
    {
        return Items[index];
    }
}

var stringLocator = new Locator<string>();

string item = stringLocator.Locate(2);
```

An additional benefit of generics is the IntelliSense provided by the editor. When you type stringLocator.Locate(4) into Visual Studio or VS Code and hover over the method name; it will show you that it returns a string instead of T. If you try to assign the result to any type other than string, the compiler will raise an error. For example, 

```csharp
// Error: Cannot implicitly convert type 'string' to 'int' [c-sharp]csharp(CS0029)
int item = stringLocator.Locate(2); 
```

A generic type can use the type parameter as a type argument when inheriting from a generic base type or a generic interface. The generic LinkedList<T> type implements the generic IEnumerable<T> interface, along with others. 

```csharp
public class LinkedList<T> : IEnumerable<T>
```

### Generic Methods

A generic method is simply a method that declares a type parameter that you can use inside the method and as parameters and return types. In the example below, Swap<T> is a generic method that takes two parameters of type T and returns an instance of T. 

```csharp
public class Swapper
{
    public T Swap<T>(T first, T second)
    {
        T temp = first;
        first = second;
        second = temp; 

        return temp;
    }
}
```

Like generic types, when you invoke a generic method, it will return a strongly typed variable. 

```csharp
var swapper = new Swapper();

int result = swapper.Swap<int>(5, 3);
```

It's possible to have multiple generic parameters. The Dictionary class in the System.Collections.Generic namespace has two type parameters, for key and value. 

```csharp
public class Dictionary<TKey, TValue>
```

Finally, it's important to know what can be generic. For types, except enums, everything can be generic. That includes:

- classes
- structs
- interfaces
- delegates

For type members, only methods and nested types can be generic. The following members can not be generic:

- Fields
- Properties
- Indexers
- Constructors
- Events
- Finalizers