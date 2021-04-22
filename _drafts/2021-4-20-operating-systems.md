---
layout: post
title: Principles of Computer System Design
img: system_design/associative_layer.jpeg
---

The book provides a broad and in-depth introduction to the main principles and abstractions for engineering computer systems, be it an operating system, a client/server application, a database system, a securre web site, or a fault-tolerant disk cluster. 

It documents the essence of client/server computing, remote procedure calls, files, threads, address spaces, best-effort networks, atomicity, authenticated messages, and so on. Fundamental ideas include design principles, modularity, naming, abstraction, concurrency, communications, fault tolerance, and atomicity. 

It identifies and develops concepts and design principles that are common to several specialty fields: software engineering, programming languages, operating systems, distributed systems, networking, database systems, and machine architecture. 

[Complexity](/system-design-principles-complexity/)

---

### Elements of Computer System Organization

Introduces three key methods of achieving and taking advantage of modularity in computer systems: abstraction, naming, and layers. It reviews the architecture and organization of computer systems in the light fo abstraction, naming, and layering. 



Vast majority of computer system abstractions fall into one of three classes:

1. Memory
2. Interpreter
3. Communication Link 

For example, the user may see the memory in the form of an organized file or database system, the interpreter in the form of a word processor, a game-playing system, or a high-level programming language, and the communication link in the form of instant messaging or the World Wide Web.

### Memory

Also known as the storage, memory is the system component that remembers data values for use in computation. It follows a simple abstract model that has two operations: 

1. WRITE (name, value)

   - Specifies a value to be remembered and a name by which one can recall that value in the future. 

2. value <- READ (name)

   - Specifies a name of some previously remembered value, and the memory device returns that value. 

**Associative Layer**

Physical implementations of memory devices nearly always name a memory cell by the geometric coordinates of its physical storage location. It is easy to design hardware that maps geometric coordinates to and from sets of names consisting of consecutive integers (0, 1, 2, etc.). These consecutive integer names are called *addresses*, and they form the *address space* of the memory device. 

For most applications, consecutive integers are not exactly the names that one would choose for recalling data. One would usually prefer to be allowed to choose less constrained or readable names. A memory system that accepts readable names is called an *associative memory*. 

Since physical memories are generally location-addressed, a designer creates an associative memory by interposing an associativity layer, which may be implemented either with hardware or software, that maps unconstrained, readable higher-level names to the constrained integer names of an underlying location-addressed memory

<a target="_blank" href="{{ site.images }}/system_design/{{ page.img }}">
  <img src="{{ site.images }}/{{ page.img }}" alt="Associative Layer">
</a>  























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