---
layout: post
title: How to remove an item from a JavaScript array? 
tags: javascript
---

Though the question is simple, I have to look it up on [StackOverflow](https://stackoverflow.com/questions/5767325/how-can-i-remove-a-specific-item-from-an-array) all the time. I could just copy-paste the answer, but that doesn't tell me what the code is doing or how it works. So here is a detailed explanation of the steps involved in removing one or more items from an array. 

Let's start with a simple array, called `numbers`. To keep things simple, we will assume that the array contains unique elements. 

```javascript
const numbers = [2, 7, 4, 9, 12, 15];
```

You want to remove the number `4` from the array. There are two steps involved. 

First, find the index of the number `4` in the array, using the [`indexOf`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf) method on the array. It returns the index of the item if it's present. Otherwise, it returns `-1`. 

```javascript
const index = numbers.indexOf(4);
```

If the number is greater than `-1`, use the [`splice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) method on the array to remove that element.

```javascript
if (index > -1) {
    numbers.splice(index, 1);
}
```

That's it. The numbers should contain following item. 
```javascript
console.log(numbers); // [2, 7, 9, 12, 15]
```

Here's the syntax of the ` splice()` method. 

```javascript
let arrDeletedItems = arr.splice(start[, deleteCount[, item1[, item2[, ...]]]])
```

It takes following parameters. 
1. `start`: The index at which to start changing the array. 
2. `deleteCount`: The number of elements to remove from `start`. 
3. `item1, item2, ...`: Elements to add in the array beginning from `start`. 

It returns the array containing the deleted elements. In our example, it will return an array that contains a single element, that was just removed. 

<p class="codepen" data-height="336" data-theme-id="dark" data-default-tab="js" data-user="akshay03" data-slug-hash="qBRyoPN" style="height: 336px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="qBRyoPN">
  <span>See the Pen <a href="https://codepen.io/akshay03/pen/qBRyoPN">
  qBRyoPN</a> by Akshay Khot (<a href="https://codepen.io/akshay03">@akshay03</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
















