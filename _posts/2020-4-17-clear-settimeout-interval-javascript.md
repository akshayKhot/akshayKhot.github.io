---
layout: post
title: Time Out
tags: programming
---

Did you know that you can cancel the scheduled execution of a `setTimeOut()` function in JavaScript? I didn't, either. Here's how it works.

Everyone knows we can schedule a piece of code to execute after some interval using `setTimeOut()`. For example, 

```javascript
function greet() {
  console.log('Hello');
}

setTimeout(greet, 1000);
```

This tells JavaScript to execute the greet function after a second has elapsed.

What if you changed your mind after setting the execution and want to cancel this call which is going to happen after a second? This is a realistic scenario, where we might want to cancel an action based on the user's input or an event.

We can use the [`clearTimeOut()`](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/clearTimeout) function to do this. According to the documentation, the `clearTimeout()` function cancels a timeout previously established by calling `setTimeout()`.

`setTimeOut()` returns a positive integer which identifies the timer created by the call to `setTimeOut()`, like this:

```javascript
let timerID = setTimeout(greet, 1000);
console.log(timerID);  // prints 2 for me!
```

We can pass this id to the `cancelTimeOut()` function to tell JavaScript that we have, indeed, changed our mind and don't want to call the `greet()` function after a second. 

```javascript
let timer = setTimeout(greet, 1000);

// life happens...

if (changedMind) {
    clearTimeout(timer);
}
```

Passing an invalid id to `clearTimeOut()` does nothing. It won't throw an error or an exception. 