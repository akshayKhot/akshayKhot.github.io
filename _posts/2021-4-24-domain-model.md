---
layout: post
title: Domain Model
---

This weekend I started yet another read of the book Domain-Driven Design by Eric Evans. These are my notes from the first chapter. It explains the concept of a domain model and how to analyze the domain to gain insights.

**What is a domain?**

Every software program relates to some activity or interest of its user. That subject area to which the user applies the program is the domain of the software.

The essence of software is its ability to solve domain-related problems for its user. All other features, however important, support this basic purpose.

Maps are models, and every model represents some aspect of reality or an idea that is of interest. A model is a simplification. It is an interpretation of reality that abstracts the aspects relevant to solving the problem at hand and ignores extraneous detail.

To create software valuably involved in users’ activities, a development team must bring to bear a body of prior business knowledge related to those activities. The breadth, volume, and complexity of this knowledge required can be daunting. Models are tools for grappling with this overload.

A model is a **selectively simplified and structured** form of knowledge. An appropriate model makes sense of information and focuses it on a problem.

In domain-driven design, three basic uses determine the choice of a model.

1. The model and the design shape each other.
2. The model is the backbone of the language used by team members to communicate with the domain experts.
3. The model is distilled and structured knowledge to identify the elements of most interest.

**When we set out to write software, we never know enough.** Knowledge on the project is fragmented, scattered among many people and documents, and it’s mixed with other information so that we don’t even know which bits of knowledge we really need. Domains that seem less technically daunting can be deceiving: **we don’t realize how much we don’t know**. This ignorance leads us to make false assumptions.

**Crunching Knowledge**

Financial analysts crunch numbers to derive the underlying meaning that can be the basis of a financial decision. Effective domain modeling tries to do the same.

Knowledge crunching is not an isolated activity. A team of developers and domain experts collaborates, typically led by developers. Together they draw in information and crunch it into a useful form. The raw material comes from:

- the minds of domain experts,
- users of existing systems,
- the prior experience of the technical team with a related legacy system or another project in the same domain.
- documents are written for the project or used in the business, and
- lots and lots of talk.

Early versions or prototypes feed experience back into the team and change interpretations.

In the old waterfall method, the business experts talk to the analysts, and analysts digest and abstract and pass the result to the programmers, who code the software. This approach fails because it completely lacks feedback from developers.

> It is the creativity of brainstorming and massive experimentation, leveraged through a model-based language and disciplined by the feedback loop through implementation, that makes it possible to find a knowledge-rich model and distill it.


This kind of *knowledge crunching* turns the knowledge of the team into valuable models.