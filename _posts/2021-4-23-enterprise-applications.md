---
layout: post
title: Characteristics of the Enterprise Applications
tags: enterprise
---

Enterprise applications often have complex data—and lots of it—to work on, together with complex business rules. In his book the [Patterns of Enterprise Application Architecture](https://www.martinfowler.com/books/eaa.html), Martin Fowler provides a few traits that differentiate enterprise applications from other software systems.

- **Persistent Data.**
  - It needs to be around between multiple runs of the program—indeed, it usually needs to persist for several years.
  - It will often outlast the software and hardware that originally created much of it, and outlast operating systems and compilers.
  - There'll be many changes to the data structure to store new information without disturbing the old details.
  - Even if there's a fundamental change and the company installs an entirely new application to handle a job, one must migrate the data to the new application.
- **Concurrent Access**
  - It depends on the organization's size, but typically many people access the data concurrently during a typical workday at the organization.
- **Lots of UI screens**
  - It's not unusual to have hundreds of different screens.
  - One must present the data in lots of different ways for different purposes.
- **Integrations with other enterprise applications**
  - One builds various systems at different times with different technologies, and the collaboration/messaging methods will be different.
  - This gets worse as businesses seek to integrate with their business partners.
- **Complicated business logic**
  - A haphazard array of abnormal conditions that often interact with each other in surprising ways.
  - Business rules are just given to you, and without significant political effort, there's nothing you can do to change them.
  - Of course, they got that way for a reason: Some salesperson negotiated to have a particular yearly payment two days later than usual because that fit with his customer's accounting cycle and thus won a couple of million dollars in business.
  - A few thousand of these one-off exceptional cases lead to the **complex business "illogic"** that makes business software tricky. In this situation, you have to organize the business logic as effectively as possible because the only sure thing is that the logic will change over time.