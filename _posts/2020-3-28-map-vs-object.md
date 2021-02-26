---
layout: post
title: Map vs. Object
tags: programming
---

Though they look similar in that both store key-value pairs, there are some important differences between a map and an object in JavaScript.

**Difference One: Map can use objects as keys**

```javascript
let person = {    
    name: 'Akshay',    
    age: 28
}
let cache = new Map();
let count = 1;
cache.set(person, count);
console.log(cache); // logs Map { { name: 'Akshay', age: 28 } => 1 }

let obj = {};
obj[person] = 1;
console.log(obj); // logs { '[object Object]': 1 }
```

**Difference Two: Map preserves the order, which is not guaranteed in an Object.**
For an example, check [this](https://stackoverflow.com/questions/5525795/does-javascript-guarantee-object-property-order) StackOverflow question.

**Difference Three: Map has a built-in forEach method.** 

```javascript
let cache = new Map();
cache.set('name', 'Akshay');
cache.set('age', 28);
cache.forEach((val, key, map) => {    
    console.log(`${key}: ${val}`);
});
```

prints

```javascript
name: Akshay
age: 28
```

The good news is, we can easily convert an existing object to a Map in two steps.

**Step One: Convert the object to an array of key-value pairs**

```javascript
let person = {
    'name': 'Akshay',
    'age': 29
}

let personArr = Object.entries(person);
// [ [ 'name', 'Akshay' ], [ 'age', 29 ] ]
```

**Step Two: Pass the array to the Map constructor**

```javascript
let cache = new Map(personArr);
// Map { 'name' => 'Akshay', 'age' => 29 }
```

The reversal from a map to an object is just a one-line code:

```javascript
let newPerson = Object.getEntries(cache);
// { name: 'Akshay', age: 29 }
```