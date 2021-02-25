---
layout: post
title: How Properties Work in C#
---

In C#, we can declare properties in a few different ways. Let's try to understand each one in detail. 

Here are various ways in which you can create a property:

```c#
public int Area => length * breadth;
```

and

```c#
public int Area = length * breadth;
```

and 

```c#
public int Area { get; set; } = 100;
```

Though they look similar, they are very different. Let's have a deeper look.

**Expression Bodied Member**

```c#
public int Area => length * breadth;
```

The first property has a **getter** under the hood that will be called each time you access the property. It is called an expression-bodied member, and it is different from a lambda expression. 

C# compiler converts an expression-bodied member to the following code. 

```c#
public int Area
{
    get
    {
        return length * breadth;
    }
}
```


**Field Initializer**

```c#
public int Area = length * breadth;
```

This is a simple field with a field initializer, which will be evaluated only once when the containing class or type is instantiated. This doesn't provide the benefits of encapsulation like properties do.

**Auto-Property Initializer**

```c#
public int Area { get; set; } = 100;
```

This initializes the property to 100. It allows us to declare the initial value of the auto-property as part of the property declaration. This makes it easier to perform the initialization exactly once. 

Properties with an initializer can be read-only. They can also be assigned in the type's constructor. They are useful in creating immutable types. 

```c#
public int Area { get; } = 100;
```