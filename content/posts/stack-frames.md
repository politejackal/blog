---
title: "Stack Frames."
date: 2026-11-21T12:00:00+03:00
draft: false
---

We will be looking at the stack from assembly's perspective. The stack is like a pile of stuff where you remove from the top first, so what goes in first comes out last, which is the LIFO (Last-In, First-Out) property of the stack (Note: FIFO is First-In, First-Out, which applies to a queue, not a stack).

Anyway, that was about the stack, but let's see the stack in detail in the computer's world. Before your local variables, the return address (pushed by the `call` instruction) and usually the saved base pointer (`rbp`) sit at the beginning of the stack frame, followed by the local variables. The stuff above the pile is empty, so you go "up" toward lower addresses—think of it like the pile's top is the lowest address and the bottom is the highest address. So as you add new stuff, it grows toward lower addresses.

When you allocate space in assembly, you move the stack pointer into the unused space (which is filled with leftover garbage values) by however many bytes you want, and then you can zero out the memory and use it. In 64-bit x86 assembly, the stack pointer is `rsp`.

To allocate space, you subtract the number of bytes you want from `rsp`. (Note: In x86 assembly, `mov rsp, rsp-8` is not a valid instruction because `mov` cannot perform arithmetic directly like that; you must use `sub` or `lea`). For example:

Code snippet

```
sub rsp, 8

```

Now you have access to eight new bytes which you didn't have before. If you want to clean (zero out) them using a simple byte-by-byte loop (Note: for 8 bytes you would normally just do `mov qword [rsp], 0`, but here is the loop you requested):

Code snippet

```
    mov rcx, 0          ; loop counter / offset
.clean_loop:
    mov byte [rsp + rcx], 0  ; zero out 1 byte at a time
    inc rcx             ; move to next byte
    cmp rcx, 8          ; have we cleared 8 bytes?
    jl .clean_loop      ; if less than 8, repeat

```

Now once you use the space, you need to be sure that you move `rsp` back to where it was before. This step is as important as the subtracting one. If you don't, the `ret` instruction at the end of the function will pop the wrong value instead of the return address, and the program will crash. (Again, `mov` cannot do addition directly, so use `add`). Here's an example:
Code snippet

```
add rsp, 8

```
