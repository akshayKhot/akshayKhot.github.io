---
layout: post
title: Smalltalk Best Practice Patterns
---

This book is about the simple things experienced, successful developers do that beginners don't. It is a style guide, in a sense, teaching you how to communicate most clearly through your code. This book is for developers who want to program and want to do so as quickly, safely, and effectively as possible. 

Best Practice: Set of procedures and skills that professionals recognize and use. 

Patterns: A decision an expert makes over and over. Even though all the results from the decision are different, the have a quality and reasoning behind them that is constant. Each pattern records a solution to a single recurring problem, including how to recognize the presence of the problem and how to generate the solution so that it fits the context. 

Development consists of two processes that feed each other. First, you figure out what you want the computer to do. Then, you instruct the computer to do it. Writing a program changes what you want the computer to do, and the cycle repeats. 

Programming doesn't happen in vaccum. We aren't always good at coming up with good design decisions. **Coding is where your fuzzy, comfortable ideas awaken in the harsh dawn of reality.** 

> Even a little help cleaning up small problems reveals the source and solution of much bigger problems.

Some of the biggest improvements come from figuring out how to eliminate:

1. Duplicate code (even little bits of it)
2. Conditional Logic
3. Complex Methods

> Too many development organizations get into a deadly embrace with their own projects, where they are spending so much time and energy just keeping the last system alive and limping that they can’t meet the needs of today’s market, much less tomorrow’s.

The bottlenecks throughout development come from limitations in human communication. When we say that 70 percent of the development budget is spent on maintenance, we mean that the poor maintainers have to wade through piles of documentation and code to discover the intent of the original programmer.

When you program, you have to think about how someone will read your code, not just how a computer will interpret it. 

**Style**

Good programming style is one of those things that everyone knows when they see it but is hard to articulate. Here are some things to look for that tell whether a project is in good shape. You should strive to have these properties in your code. 

1. Once and only once

   In a program written with good style, everything is said once and only once. 

2. Lots of little pieces

   Good code has small methods and small objects. Make sure you communicate the big picture effectively. 

3. Replacing objects

   Good style leads ot easily replaceable objects. 

4. Moving objects

   Another property of systems with good style is that hteir objects can be easily moved to new contexts. Don't try to generalize too early. Ship a couple of systems first. Then, it will be easy to generalize things. 

> Expertise in development often hinges on knowing what problems should be solved first and what problems can be safely ignored. 

Here's how to read this book. Read it all at once quickly. Then set this book on your desk as you program. Every time you are about to do anything - write a method, name a variable, name a message - look it up first. Over time, you will get into the habit of choosing the correct pattern automatically. 