---
layout: post
title: Refactoring
date: 2021-1-27
img: refactoring.jpg
---

> Whenever you read [Refactoring ], it’s time to read it again. And if you haven’t read it yet, please do before writing another line of code. - DHH

<div class="book">
<a target="_blank" href="{{ site.bookshelf }}/{{ page.img }}">
  <img src="{{ site.bookshelf }}/{{ page.img }}" alt="{{page.title}}">
</a>
</div>

**What Is Refactoring?**

Refactoring is the process of changing a software system in a way that does not alter the external behavior of the code yet improves its internal structure. In essence, when you refactor, you are improving the design of the code after it has been written.

> Refactoring (noun): a change made to the internal structure of software to make it easier to understand and cheaper to modify without changing its observable behavior.
>
> Refactoring (verb): to restructure software by applying a series of refactorings without changing its observable behavior.

With refactoring, we can take a bad, even chaotic, design and rework it into well-structured code. Each step is simple—even simplistic. Yet the cumulative effect of these small changes can radically improve the design. It is the exact reverse of the notion of software decay.

Design, rather than occurring all up front, occurs continuously during development. As you build the system, you learn how to improve the design.

A poorly designed system is hard to change—because it is difficult to figure out what to change and how these changes will interact with the existing code to get the behavior you want. And if it is hard to figure out what to change, there is a good chance that I will make mistakes and introduce bugs.


> *When you have to add a feature to a program but the code is not structured in a convenient way, first refactor the program to make it easy to understand and to add the feature, then add the feature.*

**Why Refactor?**

- Improves the design of software over time. 
- Makes the codebase easier to understand and reason about
- Helps you find bugs and program faster

**First step in Refactoring

**Make sure you have a solid set of tests for the piece of code you are refactoring. Tests are essential because the larger and complex the code, the more likely it is that your changes will break something.

Run your tests after each change you make. Testing after each change means that when you make a mistake, you only have a small change to consider in order to spot the error, which makes it far easier to find and fix. This is the essence of the refactoring process: *small changes and testing after each change.*

**During Refactoring**

When you are coding, you can have two types of understanding about what the code is doing. The first is the understanding in your head. This is fragile and temporary, residing in your short-term memory. You read code, you understand, but you forget about it a few days later. When you come back to the same code after some time, you have to again make an effort to understand the code.

The second type is the long term understanding, and it's not in your head. You persist the first type of understanding by moving it from your head to the codebase itself. By doing this, the code tells you what it's doing, and you don't have to figure it out again.

The way you do this is by extracting that piece of code into a new function and give it an intention revealing name. A name that tells you what it's doing. You can always go to that function to see *how* it's doing it, but you don't have to. You just abstracted that code to something simpler. The next time you are reading the code, you just need to glance at the name to understand what it's doing. 

Read the code, gain some insight, and use refactoring to move that insight from your head back into the code. The clearer code then makes it easier to understand it, leading to deeper insights and a beneficial positive feedback loop. 

The key to effective refactoring is recognizing that you go faster when you take tiny steps, the code is never broken, and you can compose those small steps into substantial changes.