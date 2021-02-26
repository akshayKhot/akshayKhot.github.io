---
layout: post
title: Bottlenecks in Software
tags: devops
---

In operational theory, the term **bottleneck** refers to the point in a system where Work-In-Progress (WIP) accumulates. 

A team that produces a software application has different members performing each task: writing the code, testing it, deploying it to a beta environment, and deploying it to the production environment. 

Watch what happens when a bug is reported. 

- If it sits in the bug tracking system, untouched and unassigned to anyone, the bottleneck is the triage process. 
- If it gets assigned to someone, but that person doesn’t work on the issue, the bottleneck is at the developer step. 
- If the buggy code is fixed quickly but sits unused because it hasn’t been put into testing or production, then the bottleneck is in the testing or deployment phase.

Once the bottleneck is identified, it is important to focus on fixing the bottleneck itself. There may be problems and things we can improve throughout the system, but directing effort toward anything other than optimizations at the bottleneck will not help the system's total throughput. 

- Optimizations before the bottleneck make WIP accumulate faster at the bottleneck. 
- Optimizations after the bottleneck improve the part of the process that is starved for work.

*From: Practice of System and Network Administration, The: DevOps and other Best Practices for Enterprise IT, Volume 1*