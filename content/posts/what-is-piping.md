---
title: "What Is Unix Piping?"
date: 2026-09-18T17:12:28+03:00
draft: false
---

This writeup explains what Unix piping is, and why it *might* look like a pain in the ass but *isn't*.

The thing is, you have seen many programs output stuff. But under the hood, a lot of things are going on.

Well, in linux the *text* we see going here and there, are basically divided into *input*, *output* and *error*.

Why? Well this is because under the hood, a simple program might be doing complex things and an out put which was supposed to be printed to the user as an *error* might be printed as an input for the program. I mean how would the program kknow that some text you enter in the terminal is to be treated as input, and some as output and so on? Well this is why these different channels, specifically input, output and error are needed. In this writeup I'll be focusing not on how the computer knows which is what in detail, but rather on *how we* can say the computer to treat such and such text as such and such.

Well, to learn how to use the different channels, we need to know what each channel is, even though it's quite obvious.

+ Standard *input* is the channel which takes text and processes it as input, for example, your shell uses input to process the commands you enter.
+ Standard *output* is the channel which sends out text, not as any command or so, but just as text. Example is the output you get when you are using a command like ls or "echo hello world"
+ Standard *error* is what the shell generally gives when it runs into an error. Example is the annoying text output you get saying "bash: <some_command_with_typo>: command not found".

Now getting to the interesting practical part. How do you say the computer or a program to output such and such or take such and such as input? Well, it's quite simple but useful.

**Input redirect**
You can redirect some text as input using < , for example, `cat < /etc/hostname` will output `ubuntu-server`, recall that cat takes in only files.

**Output redirect**
You can redirect something as output by using > , for example, `echo hello > output.txt` and if you `cat < output.txt` you get `hello`.


**Error redirect**
The error redirect can be done using `2>`, here 2 is for specifying the channel, and 1 stands for output channel, and by default `>` is `1>` so it outputs general text. but 2> redirects error text. For example, if you run `ls /fakefolder 2> errors.txt` without having any folder named fakefolder, you can `cat errors.txt`, and you should see something like `ls: cannot access '/fakefolder': No such file or directory`


Ofcourse there are many other cool things like changing standard output text to standard input text and all, where all this really pays off, but in this writeup I sadly won't be writing about that. Maybe next time!
