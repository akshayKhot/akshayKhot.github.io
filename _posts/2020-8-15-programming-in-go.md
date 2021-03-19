---
layout: post
title: Programming in Go
tags: random
---

Over the weekend, I have been writing a lot of Go code to automate some of the repetitive stuff I do at work, such as updating servers after grabbing the latest code from the trunk. This morning, I programmed for three hours straight from 5 to 8 am and enjoyed every minute of it. 

The more Go I write, the more I like it. Every time I make some change and hit `go run`, the compilation and execution speed brings a smile. Its simplicity continues to amaze me. There are not many moving parts in Go. Once I learned the basic syntax, I could read and understand any Go code written by anyone. I am afraid I can't say the same about C# and JavaScript/TypeScript, all of which I have been programming for over four years. In contrast, with every new release, they are getting bloated, making the languages difficult to understand and reason about. 

It's not just about writing Go. It's also about what Go enables you to do. For a long time in my career, I stayed away from systems programming, thinking it was a complicated topic for which you need to have a deep understanding of pointer arithmetic and bit twiddling. 

After browsing through a lot of Go code over the last couple of months, I am glad to find that's not the case. Of course, Go has pointers, but they are not as scary as C pointers, as there is no pointer arithmetic. You have the simple concept of a variable and its address in memory. 

Go liberates systems programming, such as server and network software, from the clutches of C and C++ and brings it to the masses, making it easier to understand and actually enjoy writing server and systems software, not just yet-another web application. 