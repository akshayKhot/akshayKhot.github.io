---
layout: post
title: Functions
tags: code
---

Since getting exposed to functional programming, I have started seeing functions everywhere.

One of the list abstractions that I never really understood was the reduce function. Whenever I came across it, my eyes just used to glaze over it. Not anymore.

Here is a simple **reduce** function that operates over a list of numbers to return the total. 

```javascript
let numbers = [1, 2, 3, 4, 5];

let total = numbers.reduce((prev, current) => prev + current, 0);
```

Here's how I can imagine a actual reduce implementation might look like, that I was able to write by thinking of functions as first-class constructs, which can be passed around like objects. 

```javascript
let numbers = [1, 2, 3, 4, 5];
let total = summarize((prev, current) => prev + current, 0);
console.log(total);

function summarize(func, start) {    
    let prev = start;
    for(let i = 0; i < numbers.length; i++) {
        let current = numbers[i];
        prev = func(prev, current);
    }
    return prev;
}
```

**Doesn't look that complicated now, does it?**