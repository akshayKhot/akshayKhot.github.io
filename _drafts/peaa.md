---
layout: post
title: Patterns of Enterprise Application Architecture
three: three_layers.jpg
net: networking_layers.png
---

This is a book on enterprise application design. Enterprise applications are about the display, manipulation, and storage of large amounts of often complex data and the support or automation of business processes with that data. Examples include reservation systems, financial systems, supply chain systems, and many others that run modern business. 

The primary topics the book explores are

- Layering of enterprise applications
- Structuring domain (business) logic
- Structuring a Web user interface
- Linking in-memory modules (particularly objects) to a relational database
- Handling session state in stateless environments
- Principles of distribution

> Choosing an architecture means that you have to understand the particular problems of your system and choose an appropriate design based on that understanding.

[Characteristics of the enteprise applications.](/enterprise-applications/)

Developers use layering to break a complicated software system into multiple parts that can be understood and analyzed independently. For example, a progrmming language is layered upon the operating system calls, which themselves are layerd upon the CPU instructions and logic gates inside chips. In networking, FTP layers upon TCP which sits on IP. 

When designing a system with layers, each layer rests on a lower layer, which is unaware of the higher layer. The higher layer uses the services provided by the lower layer. Also, each layer hides its lower layers from the layers above. 

<a target="_blank" href="{{ site.images }}/{{ page.net }}">
  <img src="/Users/akshay/Dev/akshaykhot.github.io/_drafts/{{ site.images }}/{{ page.net }}" alt="Networking Layers">
</a>  

<div class="caption"><a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/network/windows-network-architecture-and-the-osi-model">Source</a></div>

**Benefits of Layering**

1. Make a single layer easy to understand and process, without worrying about the lower layers. For example, you can understand FTP without worrying about the underlying TCP/IP protocols. 
2. Replace the layers with alternatives that has the same interface, meaning they provide the same services. 
3. Minimizing the dependencies and coupling between the layers, which makes it easy for a layer to change its internal implementation without having to modify the layer that uses it.  
4. Allows standardization and multiple higher-level uses for a lower layer. 

It's difficult to decide what layers you should have and what function each layer should perform. It's easy to design a system where introducing a change in a layer cascades into all layers. Extra unnecessary layers might affect performance, if at each boundary you need to transfer the data from one format to another. 

In general, the typical way to organize most enterprise applications is the three-layered architecture. It contains the following layers. 

<a target="_blank" href="{{ site.images }}/{{ page.three }}">
  <img src="/Users/akshay/Dev/akshaykhot.github.io/_drafts/{{ site.images }}/{{ page.three }}" alt="Three-Layered Architecture">
</a>  

- Presentation layer contains the user interface, e.g. a command-line, rich client, or a web browser. Displays the information to the user and interprets the user's commands. 
- Domain layer contains the domain logic, which is the work that the application needs to do to solve the business problems. 
- Storage layer contains the database and other data sources that the business logic needs to fetch the data from. 

---

### Organizing Domain Logic

**Transaction Script**

- A Transaction Script is essentially a procedure that takes the input from the presentation, processes it with validations and calculations, stores data in the database, and invokes any operations from other systems.
- However, there is duplicated code as several transactions need to do similar things. The application ends up being a tangled web of functinos without a clear structure. 

**Domain Model**

- Objects can help to deal with the complex logic. With a domain model, we build a model of our domain. The logic for handling validation and calculations would be placed into this domain mdodel. 
- Once you've gotten used to things, there are many techniques that allow you to handle increasingly complex logic in a well-organized way. This is where the value of a domain model lies in. 

**Service Layer**

- A service layer is an encapsulation over the domain model that provides a clear API for the users. The UI code interacts with the domain only through the service layer. 
- It's also a good place to implement transaction control and security. 
- For a simple domain model, you usually don't need a service layer. Assume you don't need one and only add it as the application gets complex. 























