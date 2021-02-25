---
layout: post
title: Functions as Objects
---

In JavaScript, functions are objects. We can not only call them, but pass them to other functions and also receive them from other functions. We can also instantiate new functions by using the **new** syntax. 

```javascript
let func = new Function ([arg1, arg2, ...argN], body);
```

The function **func** is created with the arguments as the first parameter, and the body as the second parameter. 

```javascript
let log = new Function('val', 'console.log(val)');
log('test'); // prints 'test'
```

We can also create a function that doesn't take any parameters, 

```javascript
let say = new Function(`console.log('saying')`);
say();  // prints 'saying'
```

Like objects, functions do have a few properties, including:

- **name**: returns the name of the function, or an empty string

```javascript
function log(val) {
    console.log(val);
}

log(log.name); // logs 'log'. Is your head spinning, too?
```

- **length**: returns the number of function parameters, rest parameters are not counted. 

```javascript
function log(val) {
    console.log(val);
}

log(log.length); // logs 1
```

