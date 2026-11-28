---
title: "Caller-saved vs Callee-saved Registers"
date: 2026-11-28T12:00:00+03:00
draft: false
---

When you use a register, you change its value to something else. But it might already be storing some important value which you are erasing! This matters especially when you are writing a function: whoever calls your function might have important values sitting in registers, and if your code overwrites them, their program breaks after your function returns. Here we will be assuming you are the one writing the function!

So programmers agreed on a rule. Both the caller (the one who calls the function) and the callee (the one who is called, which is you!) can use any register. The rule decides who is responsible for protecting each register's old value.

Now, the CPU doesn't enforce this. Nothing stops you from returning with a register changed. But the rule is written down in the System V ABI, the official convention for x86-64 Linux, and if you break it, you break the agreement every other programmer and hacker is relying on!

There are caller-saved registers and callee-saved registers. The callee may wipe the caller-saved registers, because the caller is supposed to save them if it still needs them. However, the callee-saved registers must come back exactly as they were before. This can be achieved in various ways. One way, and generally the most sensible one, is to push them onto the stack at the start of the function and pop them back before returning. However, because of the stack's LIFO (last in, first out) rule, you must pop them in the reverse order you pushed them!

Now here is the list of registers and which group they belong to:

| Group | Registers |
| --- | --- |
| Caller-saved (callee may wipe them) | rax, rcx, rdx, rsi, rdi, r8, r9, r10, r11 |
| Callee-saved (must be the same after return) | rbx, rbp, r12, r13, r14, r15, rsp |

(rsp is special: you don't push and pop it. It comes back to its original value as long as every push has a matching pop.)

The instructions useful for this:

- push reg: example: push rbx
- pop reg: example: pop rbx
- call func: pushes the address to return to, then goes to func!
- ret: pops an address, and jumps there!
