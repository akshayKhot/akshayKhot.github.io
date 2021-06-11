---
layout: post
title: Design Patterns in Ruby
in: design_patterns/inheritance.png
comp: design_patterns/composition.png
d_comp: design_patterns/dynamic_composition.png
---

**Separate out the things that change from those that stay the same.**

If you can identify which aspects of your system design are likely to change, you can isolate those bits from the more stable parts.

**Program to an interface, not an implementation.**

By writing code that uses the most general type possible—for example, by treating all of our planes and trains and cars like vehicles whenever we can—we reduce the total amount of coupling in our code.

**Prefer composition over inheritance.**

Instead of using inheritance,

<a target="_blank" href="{{ site.images }}/{{ page.in }}">
  <img src="{{ site.images }}/{{ page.in }}" alt="Inheritance">
</a>  

use composition, 

<a target="_blank" href="{{ site.images }}/{{ page.comp }}">
  <img src="{{ site.images }}/{{ page.comp }}" alt="Composition">
</a>  

It allows you to dynamically switch objects at runtime, like this:

<a target="_blank" href="{{ site.images }}/{{ page.d_comp }}">
  <img src="{{ site.images }}/{{ page.d_comp }}" alt="Dynamic Composition">
</a>  

**Delegate, delegate, delegate.**

Composition-delegation is a powerful and flexible alternative to inheritance. We get most of the benefits of inheritance, much more flexibility, and none of the unpleasant side effects. 

**You ain't gonna need it.** 

The YAGNI principle says simply that you should not implement features, or design in flexibility, that you don’t need right now. Why? Because chances are, you ain’t gonna need it later, either.

> Focus on the things that you need right now, building in only the flexibility that you know you need. If you are not sure that you need it right now, postpone implementing the functionality until you really do need it. If you do not need it now, do not implement it now; instead, spend your time and energy implementing the things that you definitely need right now.
