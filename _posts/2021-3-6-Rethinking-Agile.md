---
layout: post
title: Rethinking Agile
tags: cityview thoughts
---

Agile is the most common software development methodology used when building software. Ideally, it means that you don't do any big, upfront design. Instead, you work in sprints and evolve your design as your understanding of the project grows. Design is part of the programming.

This sounds nice on paper, but in reality, it's often a disaster. I have worked on some projects where I didn't do any design and planning before starting and jumped straight into the code. The final design ended up being the sum of random decisions made while in the middle of programming, which doesn't make any sense when viewed as a whole system. It ended up in rigid code, which is hard to change and evolve, which is the essence of agile and extreme programming. As time passed, more bugs crept in, and they were almost always hard to find and fix.

In contrast, there were some projects where I did plan the design of the software I was building, in turn [writing a spec](/Write-a-Spec), and they almost always turned out well. Planning in advance helps to figure out the big issues in advance and make changes if needed. Changes are always easy while designing, compared to coding.

Now, it's true that I can't think of all the issues that might come up while building software. But as [Joel says](https://www.joelonsoftware.com/2000/10/02/painless-functional-specifications-part-1-why-bother/), the goal of planning and specifying the software is not to find out **all** the details in advance, but to find out **as many as possible** to reduce the surprises when programming. 

The next question is how to plan and design software before starting coding. One way I have found really useful is to draw UML diagrams. Now, they might have been out of fashion for quite a while now, but that doesn't mean that they don't have any value. I personally, find them very useful. The important thing is to keep them simple. Draw only important classes, not all, and list only the important attributes and methods on each, and so on. 

The best thing about UML diagrams is that they allow me to capture the design. It's very hard to grasp the whole design of the system based on just looking at the code. If I come back to the code I wrote last year, it might take me a day or two to find out the core design behind the system, but a UML diagram conveys that in minutes. And I can always update them, as the design changes. 

So, to summarize, I find it useful to have both waterfall and agile mindsets when developing software. Start with a design, and revise it as I am writing code. Ultimately, that results in software that solves real problems.

