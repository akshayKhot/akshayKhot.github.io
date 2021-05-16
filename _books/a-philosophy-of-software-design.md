---
layout: post
title: A Philosophy of Software Design
date: 2021-3-4
img: philosophy_of_software_design.jpg
---

People have been programming for more than 80 years, but there has been surprisingly little conversation about how to design those programs or what good programs should look like. Though much has been written on development processes and techniques like agile and object-oriented programming, but the core problem of software design is still not explored.  

<div class="book">
  <a target="_blank" href="{{site.bookshelf}}/{{ page.img }}">
    <img src="{{site.bookshelf}}/{{ page.img }}" alt="A Philosophy of Software Design">
  </a>
  <div class="caption">A Philosophy of Software Design</div>
</div> 

Software design is never done. It is a continuous process that spans the entire lifecycle of a software system, not only the beginning. It's impossible to visualize the design for a large software system well enough to understand all of its implications before building anything. As a result, the initial design will have many problems. The problems do not become apparent until implementation is well underway.

The initial design for a system or component is almost never the best one; experience inevitably shows better ways to do things. As a software developer, you should always be on the lookout for opportunities to improve the design of the system you are working on, and you should plan on spending some fraction of your time on design improvements.

The book is based on the design principles that emerged from the class the author teaches in Stanford. The primary goal behind the book is to reduce complexity. This book is about how to use complexity to guide the design of software throughout its lifetime. 

Students learn best by writing code, making mistakes, and then seeing how their mistakes and the subsequent fixes relate to the principles. The best way to use this book is in conjunction with code reviews. When you read other people’s code, think about whether it conforms to the concepts discussed here and how that relates to the complexity of the code. 

It’s easier to see design problems in someone else’s code than your own. You can use the red flags described here to identify problems and suggest improvements. Reviewing code will also expose you to new design approaches and programming techniques. One of the best ways to improve your design skills is to learn to recognize red flags: signs that a piece of code is probably more complicated than it needs to be.

> The most fundamental problem in computer science is problem decomposition: how to take a complex problem and divide it up into pieces that can be solved independently.

---

### The Nature of Complexity

The greatest limitation in writing software is our ability to understand the systems we are creating. As programs evolve and we add new features, it becomes complicated and harder to maintain.

The ability to recognize complexity is a crucial design skill. It allows you to identify problems before you invest a lot of effort in them, and it allows you to make good choices among alternatives.

**What is Complexity?**
Complexity is anything related to the structure of a software system that makes it hard to understand and modify the system. It can take many forms, for example,

1. Change amplification: The first symptom of complexity is that a seemingly simple change requires code modifications in many different places. 
2. Cognitive load: The second symptom of complexity is cognitive load, which refers to how much a developer needs to know in order to complete a task.
3. Unknown unknowns: The third symptom of complexity is that it is not obvious which pieces of code must be modified to complete a task, or what information a developer must have to carry out the task successfully.

One of the most important goals of good design is for a system to be obvious. This is the opposite of high cognitive load and unknown unknowns. If a software system is hard to understand and modify, then it is complicated; if it is easy to understand and modify, then it is simple. In an obvious system, a developer can quickly understand how the existing code works and what is required to make a change.

Complexity is more apparent to readers than writers. If you write a piece of code and it seems simple to you, but other people think it is complex, then it is complex. Your job as a developer is not just to create code that you can work with easily, but to create code that others can also work with easily.

**What causes complexity?**
Complexity is caused by two things: **dependencies** and **obscurity**. A dependency exists when a given piece of code cannot be understood and modified in isolation, because it relates to some other code which much be changed if the given code is changed. Obscurity occurs when important information is not obvious.

Dependencies lead to change amplification and a high cognitive load. Obscurity creates unknown unknowns. Design techniques that minimize dependencies and obscurity reduce the complexity of software.

Complexity isn’t caused by a single catastrophic error; it accumulates in lots of small chunks. A single dependency or obscurity, by itself, is unlikely to affect significantly the maintainability of a software system. Complexity comes about because hundreds or thousands of small dependencies and obscurities build up over time.

**How to fight complexity?**
There are two approaches to fighting complexity. First, make code simpler and more obvious. Second, encapsulate it so that the programmer can work on a system without being exposed to all of its complexity at once. Isolating complexity in a place where it will never be seen is almost as good as eliminating the complexity entirely. 

**Strategic vs. Tactical Programming**
One of the most important elements of good software design is the mindset you adopt when you approach a programming task.

With the tactical mindset, your main focus is to get something working quickly, e.g. a new feature or a bug fix. You don't spend time looking for the best design, you just want to get something working soon. This is how systems become complicated, one small hack at a time. 

In contrast, with a strategic mindset, you invest time upfront to produce clean designs and fix problems.

Strategic approach produces better designs and is cheaper than the tactical approach over the long run.

**Tactical Tornado.** A programmer who pumps out code faster than others but leaves behind a wake of destruction. Typically, other engineers must clean up the mess left behind by these programmers.

---

### Working code isn't enough.

The most important things is the long-term structure of the system. Hence, it's not acceptable or responsible to introduce unnecessary complexities in order to finish your current task faster.

**How much to invest?**
A huge up-front investment, such as trying to design the entire system, won’t be effective. The ideal design tends to emerge in bits and pieces, as you get experience with the system. Thus, the best approach is to make lots of small investments on a continual basis.

When you are programming strategically, your initial projects will thus take 10–20% longer than they would in a purely tactical approach. That extra time will result in a better software design, and you will start experiencing the benefits within a few months. It won’t be long before you’re developing at least 10–20% faster than you would if you had programmed tactically. At this point your investments become free: the benefits from your past investments will save enough time to cover the cost of future investments. You will quickly recover the cost of the initial investment.

---

### Modules should be deep.
A software system is decomposed into a collection of modules that are relatively independent. Modules can take many forms, such as classes, subsystems, or services.**
**A module typically consists of two parts, the interface and the implementation.

**The interface** is everything that a developer working in a different module must know in order to use the given module. Typically, the interface describes what the module does but not how it does it. **The implementation** consists of the code that carries out the promises made by the interface.

In general, if a developer needs to know a particular piece of information in order to use a module, then that information is part of that module's interface.

An interface can be formal and informal. Formal interfaces include the public methods on the class or the signature of the method. Typically, these can be checked for correctness by the programming language. The informal interfaces include the high-level behavior of the system. These are larger and more complex than the formal ones. 

The best modules are those whose interfaces are much simpler than their implementation. A simple interface minimizes the complexity imposed on the rest of the system. It also reduces the impact of the change in the implementation; as long as the interface doesn't change, no other modules need to know. A clearly defined interface tells exactly what developers need to know to use the module.

**An abstraction** is a simplified view of an entity, which helps us manage complexity, by paying attention to essentials, and ignoring the irrelevant details. An abstraction can go wrong in two ways, by

1. Including details that are not really important; making the abstraction more complicated than necessary. It increases the cognitive load on developers using the abstraction. 
2. Omitting the really important details, resulting in obscurity. The developers using the abstraction won't have all the information they need to use the abstraction correctly. 

While designing abstractions, understand what is really important for your users, and look for designes that minimize the amount of information that is important.

The best modules are those that provide powerful functionality yet have simple interfaces. Interfaces should be designed to make the common case as simple as possible.

<div class="random centered">
  <a target="_blank" href="{{site.images}}/deep_modules.jpg">
    <img src="{{site.images}}/deep_modules.jpg" alt="Deep vs. Shallow Modules">
  </a>
</div>

**Shallow Modules**
A shallow module is one whose interface is complicated relative to the functionality it provides. Shallow modules don’t help much in the battle against complexity, because the benefit they provide (not having to learn about how they work internally) is negated by the cost of learning and using their interfaces. Small modules tend to be shallow.

**Classitis**
The conventional wisdom in programming is that classes should be small, not deep. We are often taught to break up larger classes into smaller ones.

**Too many simple classes tend to increase the complexity of overall system. Small classes don’t contribute much functionality, so there have to be a lot of them, each with its own interface. These interfaces accumulate to create tremendous complexity at the system level.**

---

### Information Hiding (and Leakage)

The most important technique for achieving deep modules is information hiding. 

The basic idea is that each module should encapsulate a few pieces of knowledge, which represent design decisions. The knowledge is embedded in the module’s implementation but does not appear in its interface, so it is not visible to other modules.

Some examples of information that might be hidden are: 

- How to store information in a B-tree, and how to access it efficiently. 
- How to identify the physical disk block corresponding to each logical block within a file. 
- How to implement the TCP network protocol. 
- How to schedule threads on a multi-core processor. 
- How to parse JSON documents.

Information hiding reduces complexity in two ways. 

1. It simplifies the interface to a module. 

   The interface reflects a simpler, more abstract view of the module’s functionality and hides the details.

   This reduces the cognitive load on developers who use the module.

2. Information hiding makes it easier to evolve the system.

   If a piece of information is hidden, there are no dependencies on that information outside the module containing the information, so a design change related to that information will affect only the one module.

Hiding variables and methods using `private` is not the same thing as information hiding. Though they help by preventing access, information about them can still be exposed through public methods such as getters and setters. 

**Information leakage**

It occurs when a design decision is reflected in multiple modules. This creates a dependency between them. Any change to that design decision will require changes to all of the involved modules. Information hiding can often be improved by making a class slightly larger. 

When implementations are modified, the changes often involve changes in the representation of key data structures (to improve performance, for example). Any change to that representation will result in a change to the interface, which will require modifications to all callers.

Thus, it’s important to avoid exposing internal data structures as much as possible.

**Information hiding within a class**

Try to design the private methods within a class so that each method encapsulates some information or capability and hides it from the rest of the class. In addition, try to minimize the number of places where each instance variable is used.

---

### Different Layer, Different Abstraction

Software systems are composed in layers, where higher layers use the facilities provided by lower layers. In a well-designed system, each layer provides a different abstraction from the layers above and below it; if you follow a single operation as it moves up and down through layers by invoking methods, the abstractions change with each method call.

**Pass-through Methods**

A pass-through method is one that does little except invoke another method, whose signature is similar or identical to that of the calling method. It does nothing except pass its arguments to another method, usually with the same API. It indicates that there is not a clean division of responsibility between the classes. 

Pass-through methods make classes shallower: they increase the interface complexity of the class, which adds complexity, but they don’t increase the total functionality of the system. They indicate that there is a confusion over the division of responsibility between classes. 

The solution is to refactor the classes so that each class has a distinct and coherent set of responsibilities. 

One approach, is to expose the lower level class directly to the callers of the higher level class, removing all responsibility for the feature from the higher level class.

Another approach is to redistribute the functionality between the classes. Finally, if the classes can’t be disentangled, the best solution may be to merge them.

Having methods with the same signature is not always bad. The important thing is that each new method should contribute significant functionality. Pass-through methods are bad because they contribute no new functionality.

**Pass-through Variables**

Another form of API duplication across layers is a pass-through variable, which is a variable that is passed down through a long chain of methods.

Pass-through variables add complexity because they force all of the intermediate methods to be aware of their existence, even though the methods have no use for the variables. In addition, if a new variable is added, you have to modify a large number of interfaces and methods to pass the variable through all of the relevant paths. 

Eliminating pass-through variables can be challenging. One approach is to see if there is already an object shared between the topmost and bottommost methods. If there is, then you can use that object to store all the pass-through variables. However, this object becomes the pass-through data, but at least it reduces the number of total intermediate variables. 

Another approach is to use global variabels. This elimiates the need to pass the information from method to method, but global variables almost always create other problems. For example, global variables make it impossible to create two independent instances of the same system in the same process, since accesses to the global variables will conflict.





