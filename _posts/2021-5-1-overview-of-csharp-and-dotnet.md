---
layout: post
title: Overview of C# and .NET
tags: csharp, dotnet, programming
img: dotnet/overview.png
---

Joseph Albahari's [C# 9.0 in a Nutshell](http://www.albahari.com/nutshell/) not only covers C#, but also gives a comprehensive overview of Microsoft's .NET ecosystem. It's a must-read for any developer working on the Microsoft stack. Here's a brief overview of the C# programming language and the .NET ecosystem.

C# is an object-oriented, type-safe, and general-purpose programming language that strives for programmer productivity. It tries to achieve this productivity through expressiveness, simplicity, and a focus on performance. It works on different platforms such as Windows, Mac, and Linux.

**Type-Safety:** 

C# is a statically typed language. That means the types are verified when you compile a program. This eliminates a large set of errors before the program even runs. Static typing also allows the editors to provide intellisense features to developers, thus increasing their productivity. 

**Garbage Collection:** 

Automatic memory management is an essential feature of C#. It has a garbage collector that runs along with the programs, reclaiming the unused memory. This frees the burden from programmers to explicitly deallocating memory. 

The .net ecosystem provides support for C# programs through a Common Language Runtime and Base Class Library. It also includes an application layer that provides libraries to build desktop, mobile, or web applications. 

**Common Language Runtime** 

All the languages in the .NET ecosystem, such as C#, Visual Basic, F#, and managed C++, share the runtime, hence the name Common. CLR provides garbage collection and exception handling. 

<a target="_blank" href="{{ site.images }}/{{ page.img }}">
  <img src="{{ site.images }}/{{ page.img }}" alt=".NET Runtime">
</a>  
<div class="caption">.NET Runtime</div>

C# compiler converts the code into an intermediate language (IL), similar to the byte-code for Java. The CLR then converts IL into the native code of the machine, such as X-64 or X-86, just before it’s executed. This is known as a just-in-time (JIT) compilation.

The container for this intermediate language is called an assembly. It contains information about the types along with the IL code. It allows one assembly to reference another. C# can also query the metadata using reflection. 

**Base Class Library** 

The CLR includes a set of assemblies called the base class library. It provides essential functionality needed by most of the programs, such as I/O, file/text processing, networking, etc. 

It also includes the types that the language needs itself, e.g. collection, linq, and async programming, and lets you access features of CLR such as garbage collection and reflection. 