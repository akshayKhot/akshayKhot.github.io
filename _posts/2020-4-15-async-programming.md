---
layout: post
title: Async Programming Concepts
tags: c-sharp
---

**Latency** is the amount of time required to obtain the desired result.

**Processor-bound latency** occurs when the computational task is complex; if a computation requires performing 12 billion arithmetic operations and the total processing power available is only 6 billion operations per second, at least 2 seconds of processor-bound latency will be incurred between asking for the result and obtaining it.

**I/O-bound latency,** by contrast, is latency incurred by the need to obtain data from an external source such as a disk drive, web server, and so on. Any computation that requires fetching data from a web server physically located far from the client machine will incur latency equivalent to millions of processor cycles.

"**Synchronously**" means "**using the same clock**", so when two instructions are synchronous, they use the same clock and must happen one after the other.

"**Asynchronous**" means "**not using the same clock**" so when two instructions are asynchronous, they use different clocks and can happen in parallel.

A **CPU** (central processing unit) or **core** is the unit of hardware that actually executes a given program.

A **process** is a currently executing instance of a given program. A process is represented by an instance of the Process class in the `System.Diagnostics` namespace.

Each process contains one or more threads. A `thread` is represented by an instance of the System.Threading.Thread class.

A piece of code is said to be **thread-safe** if it behaves correctly when used in a multithreaded program.

A **task** is a unit of potentially high-latency work that produces a resultant value or desired side effect. A task used to produce a value of a given type is represented by the Task<T> class, which derives from the nongeneric Task type. These can be found in the System.Threading.Tasks namespace.

A task represents a job that needs to be performed, whereas a thread represents the worker that does the job.

*From: Essential C# by Jon Skeet*