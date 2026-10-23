---
title: "What Is malloc and free?"
date: 2026-10-03T12:07:21+03:00
draft: false
---

Normal variables use *stack* memory. The compiler automatically manages the stack, but there are two major contraints:

1. Fixed sizes at compile time: Declaring a list like `int scores[100]` gives you the space for exactly 100 integers. If the user ever wants to save 101 scores, the array overflows. And if they want to use only 2 scores for 2 players, the remaining space for 98 integers gets wasted.
2. Strict scope: A local variable inside a function can never be used outside of that specific function, and it is completely wiped from memory as soon as the function returns.

`malloc` (short for memory allocate) uses `heap` memory, giving you 2 superpowers:

* Dynamic sizing: You can assign as much space you want, whenever and wherever.
* Persistent lifetime: The data stays inside the variable throughout the program, unless you decide and its time to destroy it, using the `free` function.


How do you use them in simple? Well its quite eazy!

`malloc` and `free` use a simple 4 step lifecycle. Remember it:

* Allocate memory.
* Check if you got the memory. (Because sometimes the computer might be out of memory and return NULL)
* Use.
* Free. (Using the `free()` function)

Here's a golden rule of using malloc, always use the `sizeof()` function instead of hardcoding the number of bytes you ask for in `malloc()`. For example, instead of typing 4 bytes for an integer like `malloc(4)`, use `malloc(sizeof(int)), this solves lots of problems in the future, though not necessary.

`malloc` must be used with pointers. For example,

`int score = malloc(sizeof(int))`  - this is wrong.
`int *score = malloc(sizeof(int))` - this is right.

Now using the `free()` function, very simple!

Considering the previous example where we used `malloc` to assign some memory, say we want to delete that memory so we can use it for something else, well, we just use `free(score)`. Now `score` will be equal to `NULL`.

That's it, `malloc` and `free` could be one of the most useful yet simplest functions! ;)
