---
title: "Endianness"
date: 2026-11-14T12:00:00+03:00
draft: false
---

Endianness is a very cool thing. It helps us with many things, but this writeup is not about convincing you that endianness matters, so let's go straight to what endianness is.

You see, when you enter something, like a number, say, 1234567890, it gets translated into binary of course. So you have its hex representation 0x499602d2. Now when you enter this, this travels to the computer's memory (RAM). Now let's think of this going one byte at a time. So the CPU takes the least significant byte, which is d2 in our case, and puts it into the first memory address. So now the memory looks like 0xd2, then it takes the next least significant byte, 0x02, and puts it into the next memory address. So now we have 0xd202, and so on. Then it goes on putting the thing byte by byte into memory, until we have the final bytes in memory ordered as d2 02 96 49. Now notice that the byte order is reversed. This phenomenon is known as little endianness.

And this phenomenon, of the least significant byte being stored first (at the lowest memory address), helps computers in various things, such as doing arithmetic and type casting. You can check this out in some other article deeply. Now there is also a method called big endian which stores the bytes as is in memory.

Now once you have the bytes in memory (d2 02 96 49), when you again try to use it for anything, the CPU reads it back. Because the CPU knows it is using little endian, it knows that the first byte in memory (d2) is the least significant byte, and the last byte (49) is the most significant byte, so it puts them back together in its register as 0x499602d2. So nothing affected what we typed and what we got; it just gets stored in memory in reverse byte order and helped the computer do its calculations and stuff, and many other things.

Most machines use little endian as it has some hardware advantages, but it's really not that big of a difference. Anyway, little endian is useful for you to know when you are looking at gdb or inspecting things which are in memory, because there the bytes will be stored in reverse, so you should know how to read it back as the correct value and not be confused or panic when you see it! There might be other places where knowing why things are reversed helps.
