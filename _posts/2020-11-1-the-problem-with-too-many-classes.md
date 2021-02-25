---
layout: post
title: The Problem With Too Many Clases
tags: programming 
---

John Ousterhout, in his book 'A Philosophy of Software Design' talks about the problem with having too many classes.

> The conventional wisdom in programming is that classes should be small, not deep. Students are often taught that the most important thing in class design is to break up larger classes into smaller ones.
>
> The same advice is often given about methods: “Any method longer than N lines should be divided into multiple methods” (N can be as low as 10). This approach results in large numbers of shallow classes and methods, which add to overall system complexity.
>
> The extreme of the “classes should be small” approach is a syndrome I call classitis, which stems from the mistaken view that “classes are good, so more classes are better.” In systems suffering from classitis, developers are encouraged to minimize the amount of functionality in each new class: if you want more functionality, introduce more classes.
>
> Classitis may result in classes that are individually simple, but it increases the complexity of the overall system. Small classes don’t contribute much functionality, so there have to be a lot of them, each with its own interface. These interfaces accumulate to create tremendous complexity at the system level. Small classes also result in a verbose programming style, due to the boilerplate required for each class.
>
> *Ousterhout, John. A Philosophy of Software Design (p. 26).* 

He argues that the most important issue in designing classes and other modules is to make them deep, so that they have simple interfaces for the common use cases, yet still provide significant functionality.