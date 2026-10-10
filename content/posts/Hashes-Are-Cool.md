---
title: "Hash Tables"
date: 2026-10-10T15:30:06+03:00
draft: false
---

What are hash tables? One way to build a hash table is an array of linked lists! If you are thinking what are linked lists, go check out my previous post!

So the one way to build a hash table is an array of those linked lists. Each linked list is just a part of the array. So like many linked lists.

Each element inside the array contains a pointer, and each pointer links to the first node and the first node links to the second and so on, which all then link their respective linked lists.

Hashes might come in handy when you have like almost infinite number of elements, and you might need to narrow down the results. You can use hashes for searching, for example google has almost infinite amount of data, but it still responses within a specific and short amount of time. They are using hashing too, along with other methods.

Now the main function and purpose in life of hashes. Hashes help in narrowing down results. Like a dictionary, you can use a key to to access it's value, insteaxd of searching throughout the whole bunch. It's fast, it's cool.
