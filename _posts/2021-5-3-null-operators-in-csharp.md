---
layout: post
title: Null Operators in C#
---

In C#, the `null` keyword is a literal that represents a null reference; a reference does not point to any object. When you declare a reference type variable, the compiler sets `null` as the variable's default value unless you initialize it first. This article explores the three operators C# provides to deal with the null values.

**the null-coalescing operator (??)**

Allows you to get the value of a variable if it's not null, alternatively specifying a default value. 

It replaces the following expression in C#:

```csharp
string result = value != null ? value : "default_value";
```

with the following expression.

```csharp
string result = value ?? "default_value";
```

Here is an example that illustrates this.

```csharp
using System;

string input = null;

string choice = input ?? "default_choice";

Console.WriteLine(choice);  // prints default_choice

string finalChoice = choice ?? "not_chosen";

Console.WriteLine(finalChoice);     // prints default_choice 
```

**the null-coalescing assignment operator (??=)**

It returns the value on the left side if it's not null. Otherwise, it returns the value on the right side. In other words, it allows you to initialize a variable to some default value if its current value is null.

It replaces the following expression in C#:

```csharp
if (result == null)
    result = "default_value";
```

with the following expression.

```csharp
result ??= "default_value";
```

This operator is useful with lazily calculated properties. For example:

```csharp
class Tax
{
    private Report _lengthyReport;

    public Report LengthyReport => _lengthyReport ??= CalculateLengthyReport();

    private Report CalculateLengthyReport()
    {
        return new Report();
    }
}
```


**the null-conditional operator (?.)**

This operator allows you to call a method on an instance safely. If the instance is null, it returns null instead of throwing NullReferenceException. Otherwise, it simply calls the method. 

It replaces the following expression in C#:

```csharp
string result = instance == null ? null : instance.Method();
```

with the following expression.

```csharp
string result = instance?.Method();
```

Here's an example that illustrates this. 

```csharp
using System;

string input = null;

string result = input?.ToString();

Console.WriteLine(result);  // prints nothing (null)
```

