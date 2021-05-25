---
layout: post
title: How Unix was Born
---

The following is an excerpt from the book UNIX: A History and a Memoir by Brian Kernighan, which I am reading now. It details the fascinating history of how the Unix operating system was created.

---

**CTSS** was the most innovative OP of the time, allowing users to type on terminals connected to a big IBM machine (7094), instead of punch cards. It was more pleasant and productive than batch processing.

It was such a productive programming environment that MIT researchers decided to create an even better version called **Multics,** which stood for Multiplexed Information and Computing Service.

Multics was complicated, and needed new software and hardware than IBM 7094, so MIT enlisted GE (for hardware) and Bell Labs (for software).

Because it was so ambitious, Multics soon ran into problems. It was a victim of the **second system effect**. It was over-engineered, and was described as "an attempt to climb too many trees at once." Coordinating two companies and a university spread across the country was difficult. 

> **Second system effect:** After a success, it's tempting to try to creates a new system that fixes all the remaining problems with the original while adding everybody's favorite new features. The result is often a system that's too complicated, a consequence of taking on too many different things at the same time. 

Bell Labs worked on Multics from 1966 through 1969. By 1968, it realized that it was not going to achieve its goal of providing computing services at a reasonable cost. It was too expensive. Bell Labs dropped out of the project in April 1969 (MIT and GE worked on it and Multics was eventually completed and used until 2000, though not widely).

Multics was the source of many good ideas, but its biggest contribution was its influence on a tiny operating systen called Unix. 

###  Unix

Unix was created in part as a reaction to the complexity of Multics. When Bell Labs pulled out of Multics, Ken Thompson and Dennis Ritchie who were working on it had to find something else to do. They spent time exploring ideas and doing paper designs. 

Around this time, Ken found DEC PDP-7, which was a dated computer with 16K bytes of memory. 

> “At some point I realized that I was three weeks from an operating system.” - Ken Thompson

He needed to write three programs, one per week.
1. An editor, so he could create code
2. An assembler, to turn the code into machine language that could run on the PDP-7
3. A kernel - an operating system

Right at that time, Ken’s wife went on a three-week vacation to take their one-year-old son to visit Ken’s parents in California, and Ken had three weeks to work undisturbed.

As he said during a 2019 interview, 

> One week, one week, one week, and we had Unix

The first version of a recognizable Unix system was running in mid to late 1969. 