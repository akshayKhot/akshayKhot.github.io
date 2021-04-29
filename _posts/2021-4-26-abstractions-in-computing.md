---
layout: post
title: Fundamental Abstractions in Computing
tags: cs
img: system_design/associative_layer.jpeg
layers: system_design/programming_layers.png
---

This is a brief summary of the second chapter of Principles of Computer System Design. It explores the fundamental abstractions in computing that form the basis of almost everything in hardware and software. These abstractions perform the functions of recall, processing, and communication. 

Vast majority of computer system abstractions fall into one of three classes:

1. Memory
2. Interpreter
3. Communication Link 

For example, the user may see the memory in the form of an organized file or database system, the interpreter in the form of a word processor, a game-playing system, or a high-level programming language, and the communication link in the form of instant messaging or the World Wide Web.

### Memory

Also known as the storage, memory is the system component that remembers data values for use in computation. It follows a simple abstract model that has two operations: 

1. `WRITE (name, value)`
   - Specifies a value to be remembered and a name by which one can recall that value in the future. 

2. `value <- READ (name)`
   - Specifies a name of some previously remembered value, and the memory device returns that value. 

**Associative Layer**

Physical implementations of memory devices nearly always name a memory cell by the geometric coordinates of its physical storage location. It is easy to design hardware that maps geometric coordinates to and from sets of names consisting of consecutive integers (0, 1, 2, etc.). These consecutive integer names are called *addresses*, and they form the *address space* of the memory device. 

For most applications, consecutive integers are not exactly the names that one would choose for recalling data. One would usually prefer to be allowed to choose less constrained or readable names. A memory system that accepts readable names is called an *associative memory*. 

Since physical memories are generally location-addressed, a designer creates an associative memory by interposing an associativity layer, which may be implemented either with hardware or software, that maps unconstrained, readable higher-level names to the constrained integer names of an underlying location-addressed memory

<a target="_blank" href="{{ site.images }}/{{ page.img }}">
  <img src="{{ site.images }}/{{ page.img }}" alt="Associative Layer">
</a>  

### Interpreters

These are the active elements of a computer system that perform computations. They can be described with a simple abstraction that consists of just three components:

1. An *instruction reference*, which tells the interpreter where to find its next instruction.
2. A *repertoire*, which defines the set of actions the interpreter is prepared to perform when it retrieves an instruction from the location named by the instruction reference.
3. An *environment reference*, which tells the interpreter where to find its *environment*, the current state on which the interpreter should perform the action of the current instruction.

**Processors**

A general-purpose processor is an implementation of an interpreter. The program counter contains the address of the memory location that stores the next instruction of the current program. Here is a set of instructions that our processor includes:

1. adding two numbers (ADD), 
2. subtracting one number from another (SUB), 
3. comparing two numbers (CMP), and 
4. changing the program counter to the address of another instruction (JMP).
5. read a value from memory into the register (LOAD)
6. write the value from a register into memory (STORE)

**Interpreter Layers**

Interpreters are nearly always organized in layers. The lowest layer is usually a hardware engine that has a fairly primitive set of instructions, and successive layers provide an increasingly rich or specialized instructions. 

A full-blown application system may involve three or four distinct layers of interpretation.

<a target="_blank" href="{{ site.images }}/{{ page.layers }}">
  <img src="{{ site.images }}/{{ page.layers }}" alt="">
</a>  

The lower layer typically implements an higher-level instruction by performing several instructions from teh set of next lower layer's instruction set. 

### Communication Links

Provides a way for information to move between physically separated components. The abstraction of communication links has two operations:

1. `SEND(link, outgoing_message)`: specifies an array of bits called `outgoing_message` to be sent over the `link`
2. `RECEIVE(link, incoming_message)`: accepts an incoming message over `link`.

The message is usually provided by the address and size of a buffer array in memory that contains the message.