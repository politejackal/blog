---
title: "algorithms - intro"
date: 2026-09-15T12:38:32+03:00
draft: false
---
What is an algorithm? Well in simple words, I would say an algorithm is something which takes an input and gives an output.

An example of the algorithm could be; sorting the given data. Using various algorithms such as linear search, binary search, bubble sort, merge sort, etc.

Here is an example of an algorithm:

You search on your phone contacts app for the word “John” to call him urgently.

The algorithm takes your input “John” and matches it with your contacts, and when it finds John, returns the value of his phone number. (And in the unlikely event that a contact named John doesnt exist, the algorthm maybe designed to just say something like “John is not in your contacts”).

Pretty simple right? Yes it is! Now how does the algorithm work? Well an algorithm might be going through each of your contact and checking; “Is this John?” If yes, then giving you the number, and if not, moving to the next contact and repeating the process.

However, if we have hundreds of contacts, or in some real life scenarions of going through millions of lines of data, this could be quite lengthy, isnt it? By the way, this is called linear search.

Thats when a nicely designed software comes in. It does the same thing; find John. But in a way which would require less time and less resources. For example, instead of going on one by one and checking if this is John? And then is this John?, the program could just go to the middle of the contacts and just check if John is on that middle page of the contact list, if not, it can then check if John is on the right side of the phonebook or the right. (Assuming the names are alphabetically sorted, it is.)

Then when the algorithm know that if John is on the right haf of the data, it just skips the left half all together, unlike the previous model which asked every single one if they were John. Now the problem is in half,

The program now halves the remaining half, and goes to the middle page; and checks whether John is on the page, if not then it checks if he is towards the left of this half or towards the right.

The program then halves and halves and goes on until there is either 1 page remaining, or if unlucky, 2 pages. If it is 1 page, the program just checks if John is in there, and shows his number (if not then just print something like John not found)

But if there are two pages left, the programmer would design a function in the algorithm to check the first page, then the second page. And eventually get to know John’s number (or not). This is called the binary search.

Both programs give the exact same output: John’s number (or not), but one takes less time and less resources; and notice one thing, if instead of a thousand contacts, you had 2 thousand contacts, and you used the linear search, how many more steps you might need to find a contact? A thousand more. And what if you used the binary method? Think about it for a second. Well, it takes just a single step more. Because once it halves the problem it just becomes a thousand again. Thats the beauty of it. ;)
