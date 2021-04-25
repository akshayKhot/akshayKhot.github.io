---
layout: post
title: From Information to Insights
tags: development
---

Any software project begins with incomplete knowledge and information. It is fragmented and scattered among many people and documents. The scope of this knowledge can be daunting, especially for enterprise applications. **How do you distill this knowledge to gain insights that will help build great software?**

**Domain Model**

The essence of software is its ability to solve domain problems for its user. All software relates to some activity or interest of its intended user. This activity in the real world for which the user uses the software forms the domain of the software.

> A model is a **selectively simplified and structured** form of knowledge.

To create software that provides any value to its users, developers must bring prior business knowledge related to those activities. Domain models help us tackle this complexity by simplifying details relevant to solving the problem at hand and ignoring all the irrelevant detail.

**Making Sense of Knowledge**

The information that forms the basis of the analysis comes from the minds of domain experts, users of existing systems, the prior experience of the technical team, technical and business documentation, and lots and lots of communication.

In the old waterfall method, the business experts talk to the analysts, and analysts digest and abstract and pass the result to the programmers, who code the software. This approach fails because it lacks feedback from developers. In agile teams, each iteration provides feedback to the team and constantly improves the early designs.

**Ingredients of Effective Modeling**

1. Bind the model and the implementation. 
2. Cultivate a language based on the model. 
3. Develop a knowledge-rich model. 
4. Distill the mode by removing non-essential or irrelevant concepts. 
5. Brainstorm and experiment. 

> It is the creativity of brainstorming and massive experimentation, leveraged through a model-based language and disciplined by the feedback loop through implementation, that makes it possible to find a knowledge-rich model and distill it.

Financial analysts crunch numbers to derive the underlying meaning that helps in making a financial decision. Effective domain modeling tries to do the same. Developers and domain experts collaborate and try to process the information and crunch it into a useful form.

In domain-driven design, the model and the design shape each other. The model is distilled and structured knowledge to identify the elements of most interest, allowing the team members to communicate with the domain experts.

*Source: [Domain-Driven Design](https://www.amazon.ca/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215) by Eric Evans*