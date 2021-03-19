---
layout: post
title: Reclaiming Memory
tags: random
---

In programming, [garbage collection](https://www.computerhope.com/jargon/g/garbage-collection.htm) refers to the process of programmatically cleaning up the memory allocated to objects that are not in use.

For a long time, I thought that the variables defined in a block or a function are garbage collected when the program control reaches the end of the block, or when that function returns. I was surprised to learn that it's not the case while having a fresh look at the pointers in [Go](https://golang.org/).

**A variable is garbage collected only when no path/reference to that variable exists from other members of the program**, i.e. it can no longer affect the rest of the program.

Because the lifetime of a variable is determined only by whether or not it is reachable, **a local variable may continue to exist even after its enclosing function has returned**. A simple example demonstrates this.

```go
var global *int
func f() {
    var x int
    x = 1
    global = &x
}
```

Here, x is not garbage collected when the function `f()` returns. The reason is, it's still reachable from the variable global, which is a pointer to an `int`, or `x`. As global has a reference on it, the garbage collector knows not to clean it, as it will break global, and it's allocated on a heap, not on the stack. 

```go
func g() {
    y := new(int)
    *y = 1
}
```

In contrast, when the function `g()` returns, the variable `*y` becomes unreachable and can be garbage collected, as no other variable is holding a reference to it. The compiler allocates `*y` on the stack. 

 **Why does that matter?**

In a garbage-collected language, such as `C#` or `Go,` you may wonder why knowing when a variable is garbage collected is important while programming when you have so many other things to keep in your head at the same time.

Well, though I don't need to explicitly allocate and free memory, as the GC is taking care of that, to write efficient programs I still need to be aware of the lifetime of the variables.

For example, by keeping unnecessary pointers to short-lived large objects, especially global variables, I am preventing the garbage collector from cleaning up these objects, which are taking up space, either in my RAM or on L1 or L2 cache memory. It might not matter when we have gigs of free RAM nowadays, but it does matter when programming for embedded devices where each and every byte of memory is scarce.

Now that I think of it, garbage collection seems like a wrong choice of words for such a valuable piece of data as RAM. I think **reclaiming memory** expresses the intent better, than collecting garbage. What do you think?