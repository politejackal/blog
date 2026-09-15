---
title: "algorithms - intro"
date: 2026-09-15T12:38:32+03:00
draft: false
---
what is an algorithm? well in simple words, i would say an algorithm is something which takes an input and gives an output.

an example of the algorithm could be; sorting the given data. using various algorithms such as linear search, binary search, bubble sort, merge sort, etc.

here is an example of an algorithm:

you search on your phone contacts app for the word "john" to call him urgently.

the algorithm takes your input "john" and matches it with your contacts, and when it finds john, returns the value of his phone number. (and in the unlikely event that a contact named john doesnt exist, the algorthm maybe designed to just say something like "john is not in your contacts").

pretty simple right? yes it is! now how does the algorithm work? well an algorithm might be going through each of your contact and checking; "is this john?" if yes, then giving you the number, and if not, moving to the next contact and repeating the process. 

however, if we have hundreds of contacts, or in some real life scenarions of going through millions of lines of data, this could be quite lengthy, isnt it? by the way, this is called linear search.

thats when a *nicely* designed software comes in. it does the same thing; find john. but in a way which would require less time and less resources. for example, instead of going on one by one and checking if this is john? and then is this john?, the program could just go to the middle of the contacts and just check if john is on that middle page of the contact list, if not, it can then check if john is on the right side of the phonebook or the right. (Assuming the names are alphabetically sorted, it is.)

then when the algorithm know that if john is on the right haf of the data, it just skips the left half all together, unlike the previous model which asked every single one if they were john. now the problem is in half,

the program now halves the *remaining* half, and goes to the middle page; and checks whether john is on the page, if not then it checks if he is towards the left of this half or towards the right.

the program then halves and halves and goes on until there is either 1 page remaining, or if unlucky, 2 pages. if it is 1 page, the program just checks if john is in there, and shows his number (if not then just print something like john not found)

but if there are two pages left, the programmer would design a function in the algorithm to check the first page, then the second page. and eventually get to know john's number (or not). this is called the binary search.

both programs give the exact same output: john's number (or not), but one takes less time and less resources; and notice one thing, if instead of a thousand contacts, you had 2 thousand contacts, and you used the linear search, how many more steps you might need to find a contact? a thousand more. and what if you used the binary method? think about it for a second. well, it takes just a *single* step more. because once it halves the problem it just becomes a thousand again. thats the beauty of it ;)

