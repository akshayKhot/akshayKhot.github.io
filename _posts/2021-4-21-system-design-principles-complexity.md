---
layout: post
title: "Principles of Computer System Design: Complexity"
tags: cs
---

This article is a summary and a collection of my notes from the first chapter of Jerome H. Saltzer’s book [Principles of Computer System Design](https://ocw.mit.edu/resources/res-6-004-principles-of-computer-system-design-an-introduction-spring-2009/online-textbook/). It introduces the concept of a system, the causes of complexity in systems, and a few ways to deal with the complexity.

### Systems

1. The importance of systematic design principles and gaining a 'systems perspective'.
2. The role of modularity in controlling the complexity of large systems, 
3. The methods of enforcing modularity

To design and develop applications that support fault tolerance, concurrency, distribution, storage, security, and multi-user interaction, the designer must look beyond the software and hardware and view the computer system as a whole. 

The study of systems is one place where computer engineering can take advantage of knowledge from other engineering areas: 

- civil engineering (bridges and skyscrapers), 
- urban planning (the design of cities), 
- mechanical engineering (automobiles and air conditioning), 
- aviation and space flight, 
- electrical engineering, and even 
- ecology and political science.

**Common Problems of Systems**

1. Emergent Properties
   - Properties that are not evident in the individual components of a system, but show up when those components are combined. 
   - Some things show up only when a system is built. 
2. Propagation of Effects
   - In a complicated system, as a change is introduced, more distant and subtle effects normally appear. 
3. Incommensurate Scaling
   - As a system increases in size or speed, not all parts of it folllow the same scaling rules, so things stop working. Different parts of the system exhibit different orders of growth. 
   - It is usually the factor that limits the size or speed range that a single system design can handle. 
4. Trade-offs
   - Pushing down on a problem at one point causes another problem to pop up somewhere else. 
   - Much of a system designer's intellectual effort goes into evaluation various kinds of trade-offs. 

**A system is a set of interconnected components that has an expected behavior observed at the interface with its environment.**

The underlying idea of a system is to divide all things into two groups:

1. those under discussion 
2. those not under discussion

To analyze a system one must establish a point of view to determine which things to consider as components, what the granularity of those components should be, where the boundary of the system lies, and which interfaces between the system and its environment are of interest.

**Complexity**

Lack of systematic understanding is the underlying feature of complexity. Here are five signs of complexity.

1. A large number of components
2. A large number of interconnections
3. Many irregularities. Exceptions complicate understanding
4. A long description
5. A team of designers, implementers, or maintainers

**Sources of Complexity**

1. Cascading and interacting requirements
   - Accumulation of many requirements adds not only their individual complexities but also complexities from their interactions. 
   - This interaction complexity arises from pressure for generality and exceptions that add complications and is made worse by a change in individual requirements over time. 
2. Maintaining high utilization
   - A desire for high performance or efficiency is frequently a specific source of complexity. 
   - The more one tries to increase utilization of a limited resource, the greater the complexity. 

> Design Principle: **Avoid Excessive Generality**. If it's good for everything, it's good for nothing. 

> Design Principle: **The Law of Diminishing Returns**. The more one improves some measure of goodness, the more effort the next improvement will require. 



**Coping with Complexity**

- Modularity

  - Analyze or design the system as a collection of interacting subsystems or modules. 
  - Allows you to think about the components and their interactions inside a module in isolation while ignoring the other modules. 
  - Decomposing a system into modules allows us to replace a bad module with a good one, which incrementally improves the system without completely rebuilding it. 

- Abstraction

  - Separation of interface from internals, of specification from implementation.
  - Well designed and properly enforced modular abstractins are important in limiting the impact of faults because they control propagation of effects.  

- Layering

  - Building on a set of mechanisms already complete and using them to create a different complete set of mechanisms. 

- Hierarchy

  - Starting with a small group of modules, assemble them into a stable, self-contained subsystem with a well-defined interface. Next, assemble a small group of subsystems to produce a larger subsystem.
  - This process continues until the final system has been constructed from a small number of large subsystems. The result is a hierarchy. 

- Iteration

  - Start by building a simple, working system that meets only a modest subset of the requirements and then evolve that system in small steps to gradually encompass more and more of the full set of requirements. 

  - Small steps can help reduce the risk that complexity will overwhelm a system design. 

> You won't get it right the first time, so make it easy to change. 



