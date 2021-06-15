---
layout: post
title: Design Patterns in Ruby
in: design_patterns/inheritance.png
comp: design_patterns/composition.png
d_comp: design_patterns/dynamic_composition.png
tmp: design_patterns/template_method.png
---

This morning, I started a read of Russ Olson's excellent [Design Patterns in Ruby](https://learning.oreilly.com/library/view/design-patterns-in/9780321490452/). Since Ruby is such a readable and simple langugage, understanding the design patterns boils down to their core, without getting bogged down in the complexities of a language like Java. I am definitely having a better time reading this book, rather than the original [gang-of-four](https://learning.oreilly.com/library/view/design-patterns-elements/0201633612/) tome. 

**Ruby is a meritocracy**

This “I am what I am” approach to typing has been called **duck typing.** The name comes from the old bit of wisdom that goes, “If it looks like a duck and quacks like a duck, then it is a duck.” 

Another way to look at this issue is to think of static typing as working like an aristocracy: Statically typed languages are constantly asking about your parent or grandparent, or perhaps, in the case of Java-style interfaces, your aunts and uncles. 

In a statically typed language, an object’s family tree matters deeply. Dynamically typed languages, by contrast, are meritocracies: They are concerned with which methods you have, rather than where those methods came from. 

Dynamically typed languages rarely ask about an object’s ancestry; instead, they simply say, “I don’t care who you are related to, Mac. All I want to know is what you can do.”

**Separate out the things that change from those that stay the same.**

If you can identify which aspects of your system design are likely to change, you can isolate those bits from the more stable parts.

**Program to an interface, not an implementation.**

By writing code that uses the most general type possible—for example, by treating all of our planes and trains and cars like vehicles whenever we can—we reduce the total amount of coupling in our code.

**Delegate, delegate, delegate.**

Composition-delegation is a powerful and flexible alternative to inheritance. We get most of the benefits of inheritance, much more flexibility, and none of the unpleasant side effects. 

**You ain't gonna need it.** 

The YAGNI principle says simply that you should not implement features, or design in flexibility, that you don’t need right now. Why? Because chances are, you ain’t gonna need it later, either.

> Focus on the things that you need right now, building in only the flexibility that you know you need. If you are not sure that you need it right now, postpone implementing the functionality until you really do need it. If you do not need it now, do not implement it now; instead, spend your time and energy implementing the things that you definitely need right now.