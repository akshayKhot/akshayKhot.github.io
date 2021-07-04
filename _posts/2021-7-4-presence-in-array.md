---
layout: post
title: Freedom to Choose
tags: ruby
---

One thing I love about Ruby is that it allows multiple ways to accomplish same things, without forcing you to choose one. You can choose any approach that fits the context and write readable code.

Let's consider the common example of searching for a presence of a value in an array. Ruby provides two options that let you do the same. 

1. `includes`

   ```ruby
   if people.include? person
   ```

2. `in`

    ```ruby
    if person.in? people
    ```

Both the options accomplish the same goal: check if a person exists in the people array. However, depending on the context and the focus of the code, you can choose one or the other. 

This is drastically different from one of the core values of Python. 

> There should be one-- and preferably only one --obvious way to do it.

I prefer the ruby way. 
