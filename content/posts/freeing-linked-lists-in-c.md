---
title: "Freeing Linked Lists in C Problem"
date: 2026-10-16T22:34:44+03:00
draft: false
---

Problem Code (chain.c):

```#include <stdio.h>
#include <stdlib.h>

typedef struct node
{
    int id;
    struct node *next;
} node;

// =========================================================
// THE 5-MINUTE CHALLENGE: 
// Fix this loop so Valgrind reports 0 errors and 0 leaks.
// =========================================================
void free_list(node *head)
{
    node *cursor = head;
    while (cursor != NULL)
    {
        free(cursor);
        cursor = cursor->next; // <-- BUG: Reading memory we just freed!
    }
}

int main(void)
{
    // Build a simple 3-node list: [1] -> [2] -> [3] -> NULL
    node *n1 = malloc(sizeof(node));
    node *n2 = malloc(sizeof(node));
    node *n3 = malloc(sizeof(node));

    n1->id = 1; n1->next = n2;
    n2->id = 2; n2->next = n3;
    n3->id = 3; n3->next = NULL;

    free_list(n1);
    return 0;
}```

Valgrind Error:

```
==72347== Memcheck, a memory error detector
==72347== Copyright (C) 2002-2024, and GNU GPL'd, by Julian Seward et al.
==72347== Using Valgrind-3.26.0 and LibVEX; rerun with -h for copyright info
==72347== Command: ./chain
==72347== 
==72347== Invalid read of size 8
==72347==    at 0x4001193: free_list (chain.c:20)
==72347==    by 0x4001229: main (chain.c:35)
==72347==  Address 0x4a9f048 is 8 bytes inside a block of size 16 free'd
==72347==    at 0x48538BF: free (vg_replace_malloc.c:990)
==72347==    by 0x400118E: free_list (chain.c:19)
==72347==    by 0x4001229: main (chain.c:35)
==72347==  Block was alloc'd at
==72347==    at 0x4850858: malloc (vg_replace_malloc.c:447)
==72347==    by 0x40011BB: main (chain.c:27)
==72347== 
==72347== 
==72347== HEAP SUMMARY:
==72347==     in use at exit: 0 bytes in 0 blocks
==72347==   total heap usage: 3 allocs, 3 frees, 48 bytes allocated
==72347== 
==72347== All heap blocks were freed -- no leaks are possible
==72347== 
==72347== For lists of detected and suppressed errors, rerun with: -s
==72347== ERROR SUMMARY: 3 errors from 1 contexts (suppressed: 0 from 0)
```

Awesome challenge, credits to Gemini 4 Argon :)

My brain's POV ;)

~ I saw that the memory which is being accessed was being freed before using it, quite obvious!

~ Why not use a temporary copy of the variable that we want? Awesome, I made a tmp variable.

~ Then I quite bravely freed the cursor variable. 

~ And finally to make the linked list point to the new element, I used `cursor = tmp.next;`.

EASY PEASY!

Ummm so yeah the code and the output of valgrind now look like:


chain.c:

```
#include <stdio.h>
#include <stdlib.h>

typedef struct node
{
    int id;
    struct node *next;
} node;

void free_list(node *head)
{
    node *cursor = head;
    while (cursor != NULL)
    {
        node tmp = *cursor;
        free(cursor);
        cursor = tmp.next; // <-- BUG: Reading memory we just freed!
    }
}

int main(void)
{
    // Build a simple 3-node list: [1] -> [2] -> [3] -> NULL
    node *n1 = malloc(sizeof(node));
    node *n2 = malloc(sizeof(node));
    node *n3 = malloc(sizeof(node));

    n1->id = 1; n1->next = n2;
    n2->id = 2; n2->next = n3;
    n3->id = 3; n3->next = NULL;

    free_list(n1);
    return 0;
}
```

Valgrind Output:

```
==72513== Memcheck, a memory error detector
==72513== Copyright (C) 2002-2024, and GNU GPL'd, by Julian Seward et al.
==72513== Using Valgrind-3.26.0 and LibVEX; rerun with -h for copyright info
==72513== Command: ./chain
==72513== 
==72513== 
==72513== HEAP SUMMARY:
==72513==     in use at exit: 0 bytes in 0 blocks
==72513==   total heap usage: 3 allocs, 3 frees, 48 bytes allocated
==72513== 
==72513== All heap blocks were freed -- no leaks are possible
==72513== 
==72513== For lists of detected and suppressed errors, rerun with: -s
==72513== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)

```

If you are reading this, buy a coffee for me... idk how...
