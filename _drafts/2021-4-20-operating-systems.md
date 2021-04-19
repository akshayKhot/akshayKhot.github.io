---
layout: post
title: Principles of Computer System Design
---

The book provides a broad and in-depth introduction to the main principles and abstractions for engineering computer systems, be it an operating system, a client/server application, a database syste, a securre web site, or a fault-tolerant disk cluster. 

It documents the essence of client/server computing, remote procedure calls, files, threads, address spaces, best-effort networks, atomicity, authenticated messages, and so on. Fundamental ideas include design principles, modularity, naming, abstraction, concurrency, communications, fault tolerance, and atomicity. 

It identifies and develops concepts and design principles that are common to several specialty fields: software engineering, programming languages, operating systems, distributed systems, networking, database systems, and machine architecture. 

---

### Systems

Introduces three main ideas

1. The importance of systematic design principles, and gaining a 'systems perspective'
2. The role of modularity in controlling complexity of large systems, 
3. The methods of enforcing modularity

To design and develop applications that support fault tolerance, concurrency, distribution, storage, security, and multi-user interaction, the designer must look beyong the software and hardware and view the computer system as a whole. 

The study of systems is one place where computer engineering can take advantage of knowledge from other engineering areas: 

- civil engineering (bridges and skyscrapers), 
- urban planning (the design of cities), 
- mechanical engineering (automobiles and air conditioning), 
- aviation and space flight, 
- electrical engineering, and even 
- ecology and political science.



> Keep It Simple, Silly. 



**Common Problems of Systems**

1. Emergent Properties
   - Properties that are not evident in the individual components of a system, but show up when those components are combined. 
   - Some things show up only when a system is built. 
2. Propagation of Effects
   - In a complicated system, as a change is introduced, more distant and subtle effects normally appear. 
3. Incommensurate Scaling
   - As a system increases in size or speed, not all parts of it folllow the same scaling rules, so things stop working. Different parts of teh system exhibit different orders of growth. 
   - It is usually the factor that limits the size or speed range that a single system design can handle. 
4. Trade-offs
   - Pushing down on a problem at one point causes another problem to pop up somewhere else. 
   - Much of a system designer's intellectual effort goes into evaluation various kinds of trade-offs. 

**A system is a set of interconnected components that has an expected behavior observed at the interface with its environment.**

The underlying idea of a system is to divide all things into two groups:

1. those under discussion 
2. those not under discussion

---

### Elements of Computer System Organization

Introduces three key methods of achieving and taking advantage of modularity in computer systems: abstraction, naming, and layers. 

---

### Design of Naming Schemes

---

### Enforcing Modularity with Clients and Services

Introduces the powerful and widely used method of allowing modules to interact without interfering with one another. 

---

### Enforcing Modularity with Virtualization

Introduces the virtual memory and threads. 

---

### Performance

Focuses on intrinsic performance bottlenecks that are found in common across many kinds of computer systems, including operating systems, databases, networks, and large applications. 