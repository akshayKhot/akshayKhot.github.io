---
layout: post
title: Infrastructure as Code
tags: devops
---

In an IaC environment, we don’t make changes to systems directly. Instead, we update the code and data that are used to create our environments.

When we administer systems this way, the code we use to control our infrastructure is not just part of our infrastructure; it *is* our infrastructure. It describes the network connections between machines, the machines themselves, and the applications that run on the machines.

To create a new machine, we update our machine-processable description and let the automation create it. If we do not like that change, we can revert to a previous version of that machine-processable description. We fix our infrastructure as a developer fixes a bug: We make a change to code and test it in a test environment; if that is successful, we push the change to production.

When we manage our infrastructure as code, every change would be made by updating machine-processable definition files that, when processed, created machines, deleted machines, configured systems, created files, started processes, and so on. We would gain the ability to track changes, know the history of our infrastructure, and identify who made which change. Our infrastructure would be parameterized so that we could build the same environment with different quantities, names, and locations. System administration could reap the benefits that software engineers have enjoyed for decades.

**Benefits** 

- Reduced Cost: Manual labour is reduced or eliminated. Automation is a workforce multiplier: It permits one person to do the work of many. 
- Improved Speed: Not only can tasks be done faster, but they can also be done in parallel. They can be done without waiting for a person to be available to do the work. 
- Reduced Risk: Security risk is reduced because we can prove compliance. We can reduce the risk of errors and bugs by applying software engineering techniques like unit tests and version control. 

**Principles** 

- Make all changes via configuration files, such as a Dockerfile or PowerShell scripts.
- Document systems and processes in code to make it the source of truth. 
- Use a version control system to track changes in the configuration files. 

It can be intimidating to get started with IaC, especially in a preexisting environment. The best strategy is to start small. Automate one thing on one machine to get comfortable. Then manage more aspects of the system over time and build toward an environment where all changes are made via the CM system.

*From:* [*Practice of System and Network Administration*](https://www.amazon.ca/Practice-System-Network-Administration-Enterprise-ebook/dp/B01MFCSNQZ/ref=sr_1_1?dchild=1&keywords=Practice+of+System+and+Network+Administration%2C+The%3A+DevOps+and+other+Best+Practices+for+Enterprise+IT%2C+Volume+1&qid=1600958358&sr=8-1)