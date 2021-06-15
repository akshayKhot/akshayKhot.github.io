---
layout: post
title: Composition over Inheritance
in: design_patterns/inheritance.png
comp: design_patterns/composition.png
d_comp: design_patterns/dynamic_composition.png
---

Inheritance is more rigid as most languages do not allow you to derive from more than one type. With composition, it's easy to change behavior on the fly with Dependency Injection / Setters. 

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