---
layout: post
title: Delegates in C#
tags: programming
---

Delegates in C# was one of the many concepts that eluded me for a long time. Not anymore. I started reading C# in Depth by Jon Skeet this morning, and the entire first chapter is devoted to delegates. It really dives deep into delegates. Here's a brief summary.

**What are delegates?**

If you are a C programmer, then delegates can be thought of as function pointers. That is, a delegate can be seen as a placeholder for a function. However, delegates in C# are much more than a simple function pointer.

Essentially, delegates provide a level of indirection. They encapsulate and abstract a behaviour to be executed. Instead of executing the behaviour immediately, it is contained in an object. There are multiple actions that you can perform on that object, and one of them is executing that contained behaviour.

**When to use delegates?**

Delegates are typically used when the code that wants to execute some actions doesn’t know the details of what those actions should be but knows the interface of those actions.

In programming, we are often faced with situations where we need to execute a particular action, but we don’t know in advance which method we will want to call upon to execute it. Delegates help us solve this problem by replacing that behaviour with a delegate and then passing a concrete instance of that delegate with the appropriate behaviour as needed by the context and the situation.

**How to use delegates?**

In order for a delegate to do anything, four things need to happen:

**1) The delegate type needs to be declared.**

A delegate type is essentially the definition of the function it’s representing, i.e. it consists of the parameter types the function will accept and a return type that it returns.

For instance, a delegate type that represents a method that takes two numbers as input and returns a number can be declared as:

```c#
delegate int Processor(int numOne, int numTwo)
```

`Processor` is a type, similar to a type created by a class. To create an instance of this type, you need a method that takes two numbers as input and returns a bool.

**2) The code to be executed must be contained in a method.**

Define a method that does has the exact same signature as the above delegate type and that does what you want according to the situation at runtime. For example, any of the following methods can be used to create an instance of Processor, as they all take two numbers and return a number.

```c#
int Add(int numOne, int numTwo)
{
    return numOne + numTwo;
}

int Subtract(int numOne, int numTwo)
{
    return numOne - numTwo;
}
```

**3) A delegate instance must be created.**
Now that you have a delegate type and a method with the right signature, you can create an instance of that delegate type. In doing this, we are essentially telling the C# compiler to execute this method when the delegate instance is invoked.

```c#
Processor processorOne = new Processor(Add);
Processor processorTwo = new Processor(Subtract);
```

The above example assumes that the Add and Subtract methods are defined in the same class where we are creating the instance of the delegate. If the methods are defined in a different class, we would need the instance of that class.

**4) The delegate instance must be invoked.**
This is just a matter of calling a method on the delegate instance, which is named, not surprisingly, Invoke. This method on the delegate instance has the same list of parameters and return type that the delegate type declaration specifies. Calling Invoke will execute the action of the delegate instance.

```c#
int sum = processorOne.Invoke(3, 5); 
```

However, C# makes it even easier. You can directly invoke the delegate instance as if it was a method in itself. For example,

```
int difference = processorTwo(10, 6);
```

**Combining and Removing Delegates**
If we want to execute a list of different actions with a single invocation of a delegate instance, C# allows us to do that. The System. Delegate type has two static methods, called Combine and Remove.


 **1. Combine**

Creates a new delegate with an invocation list that concatenates the invocation lists of the delegates passed as parameters. When the new delegate instance is invoked, all its actions are executed in order.

```c#
public static Delegate Combine(params Delegate[] delegates); // OR
public static Delegate Combine(Delegate a, Delegate b);
```

If any of the actions in the invocation list throws an exception, that prevents any of the subsequent actions from being executed.

 **2. Remove**
Removes the last occurrence of the invocation list of a delegate from the invocation list of another delegate. Returns a new delegate with an invocation list formed by taking the invocation list of source and removing the last occurrence of the invocation list of value.

```c#
public static Delegate Remove(Delegate source, Delegate value);
```

**Summary**

- Delegates encapsulate behaviour with a particular type and set of parameters, similar to a single-method interface.
- The type signature described by a delegate type declaration determines which methods can be used to create delegate instances and the signature for invocation.
- Creating a delegate instance requires a method that we would like to execute when the delegate is invoked.
- Delegate instances are immutable, similar to strings.
- Delegate instances each contain an invocation list - a list of actions.
- Delegate instances can be combined with and removed from each other.

Source: [C# in Depth](https://www.amazon.ca/C-Depth-Jon-Skeet/dp/161729134X/ref=sr_1_2?keywords=c%23+in+depth&qid=1561315882&s=gateway&sr=8-2), Jon Skeet