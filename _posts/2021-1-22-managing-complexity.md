---
layout: post
title: Managing Complexity
tags: development
---

Software development is difficult. Especially if you are working on a 25-year old enterprise software that has gone through multiple platforms, technologies, and has seen multiple generations of developers. All of which makes it really hard to understand and difficult to develop. 

As a developer, I spend a lot of time writing code. But I spend even more time maintaining that code. Often, I go back to the code I wrote just a week ago and find it a tangled mess that I cannot understand. Over time, entropy kicks in, and the code becomes so complicated that it’s hard to even know what I was thinking when I wrote it.

In his landmark paper titled [**No Silver Bullets**](https://ieeexplore.ieee.org/document/1663532), Fred Brooks describes two types of complexities that make software development difficult. 

**Essential complexity**

This is the complexity inherent to the software and the problem it's trying to solve. Characteristics that a piece of software must have, to be that software. This includes a complex domain and complicated business logic.

**Accidental complexity**

The complexity that creeps in during the process of software development that is not related to the problem. Often, it is caused by poor communication between team members, not understanding the problem, and lack of training and/or experience of the developers. 

In his classic book **Code Complete**, Steve McConnell argues that **Managing Complexity** is the most important technical topic in software development, making it the software’s primary technical imperative. He provides a two-part approach to managing complexity.



1. Minimize the amount of essential complexity that a developer’s brain has to deal with at any one time. 
2. Keep accidental complexity from needlessly proliferating.

Based on these principles, there are a few techniques we can use to reduce complexity.

**Isolate**

Don't try to cram the whole program into our heads at once. Instead, organize them in such a way that we can safely focus on one part of it at a time. The goal is to minimize the amount of a code you have to think about at any one time.

**Divide and Conquer**

To reduce the complexity, divide the complicated problem into sub-problems, which are themselves simple and independent. This makes it safe to focus on one thing at a time.

**Abstractions**

Write programs in terms of the problem domain, rather than in terms of low-level implementation details. Working at the highest level of abstraction reduces the load on your brain.

**Simplify**

Avoid making clever designs. They are hard to understand. Instead, make ‘simple’ and ‘easy-to-understand’ designs. If your design doesn’t let you safely ignore most other parts of the program when you are immersed in one specific part, the design isn’t doing its job.

**Reusability**

Design the system so that you can reuse pieces of it in other systems. Refactor the duplicated code into functions, or group related code into a class or a module. 

**Non-leaky Abstraction**

This is the concept introduced by Joel Spolsky in his article, [The Law of Leaky Abstractions](https://www.joelonsoftware.com/2002/11/11/the-law-of-leaky-abstractions/). Try to design and build the software in such a way so that you can view the system at any single level and get a consistent view, without dipping into other levels.

**Information Hiding**

Asking ‘what details and information should I hide?’ solves many difficult design issues. The client of a program should be shielded from the internal workings of a program. 

The many challenges involved in building working software are what makes the activity so much fun, and a worthwhile pursuit to follow. If it was easy, it wouldn’t be fun, either. So I guess we are better off embracing and managing this complexity. 

Happy coding!



