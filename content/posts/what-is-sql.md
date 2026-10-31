---
title: "What is SQL?!"
date: 2026-10-31T12:00:00+03:00
draft: false
---

SQL (Structured Query Language) is a language to communicate with relational databases. Instead of managing complex data structures manually, you use SQL to easily store, search, and update large amounts of information. The use of SQL is pretty straightforward, in the sense that its not in much of a cryptic style. In this writeup, we will be looking at SQLite, which is a lightweight database engine that uses SQL as you can probably guess.

The following explains in brief how you use SQL:

In SQL the language expects you to select what data you want. But before that, you must know how data is stored in a database. The following explains in brief how data is stored:

The data is divided into tables. You can specify the tables you want. Each table has columns.

Each column, for example, name or age, contains whatever data you store.

Each individual thing's, or person's information in our case, is stored in a row.

Now that you know how the data is stored, lets access it!

So when you tell SQL what you want, you SELECT the data. By simply typing in SELECT. Followed by the column you want. For example: SELECT name

Then you specify the table from which you are selecting, by using the FROM command, which is followed by the name of the table you want. Example: SELECT name FROM people

Either you can end your query over here or you can specify many other things, like ORDER BY to sort the data in some ascending or descending order, and much more stuff. Example: SELECT name FROM people ORDER BY name DESC (DESC is short for descending, and ASC for ascending). This is generally the last command of the statement.

You can additionally also specify certain conditions for the data like an if statement using the WHERE clause. You follow it by the condition you want. For example: SELECT name FROM people WHERE name = 'Tommy'

There are many other things you can do in SQL, but for now, lets look at a critical thing in SQL, which is a semicolon. Every SQL statement must end with a semicolon as in C.

So a final example would be (this contains something called a wildcard, you will know about this when you learn it of course!):

SELECT name FROM people WHERE name LIKE 'Tommy%' ORDER BY name ASC;
