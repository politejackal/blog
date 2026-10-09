---
title: "Linked Lists in C Are SO Annoying"
date: 2026-10-09T23:19:05+03:00
draft: false
---

Linked lists are known to be notoriously annoying. I have been stuck on them for a few days now. But, today I finally got it.

So, a linked list is basically a list, which just stores the address of a node. Now what is a node, a node is something which contains whatever the data you like, but in addition to it it also contains a pointer to say like where the next piece of data is. A linked list is just a pointer to the first node, after the first node the story goes on, the next node to which the first node was pointing also has a pointer to the next, and some data whatever you like, of course.

So you might picture this in your mind, that we are talking about something which goes like +---- >---->---->---->----> or something, where the first character, + is the list.  Yeah that's what it is. One node linking the other. Now we can store something and also point to another piece of data. Now why might we do that? Recall that an array is a bunch of bytes in a memory, if we cant get those bytes in order, we might never be able to create an array, even if we have lots of space left on our device, but just not in order. So to solve this problem, we can use linked lists.

A linked list might be like a list which just contains a pointer to the first node, whch contains some data and another value, the pointer. And the pointer points to another node, which in turn does the same thing. This solves the memory problem because pointers go to the exact address and dont need to be in order.

But they come at a price. We will need to store the pointer to the next node in every node. But its still fine, at least we are able to get a type of list!

NOTE: If you ever loose the first list of the linked list, which contains the pointer to the first node, how can you continue or get the rest of the parts of the nodesat least or recover them? YOU CAN'T!! So be careful. :)
