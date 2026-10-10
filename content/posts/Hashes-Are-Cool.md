---
title: "Hash Tables"
date: 2026-10-10T15:30:06+03:00
draft: false
---
The main purpose in life of a hash table: finding things fast. Like a dictionary, you use a key to access its value, instead of searching through the whole bunch. It’s fast, it’s cool.

How does it know where to look? A hash function turns the key into a number, and that number tells you which slot in the array to go to.

One way to build a hash table is an array of linked lists! If you’re wondering what linked lists are, go check out my previous post! Each slot in the array contains a pointer to the first node of a linked list, the first node links to the second, and so on. If two keys end up in the same slot, they just go into the same list.

Hash tables come in handy when you have an almost infinite number of items. For example, Google has an enormous amount of data but still responds in a short amount of time. They use hashing too, along with other methods.
