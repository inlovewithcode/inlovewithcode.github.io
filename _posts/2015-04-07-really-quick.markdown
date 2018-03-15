---
author: guidedmissile
comments: true
date: 2015-04-07 05:32:08+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/04/07/really-quick/
slug: really-quick
title: Really quick - Cycle Sort
wordpress_id: 262
categories:
- Python
tags:
- Algorithms
---

Source: [GeeksForGeeks.org](http://www.geeksforgeeks.org/fundamentals-of-algorithms/)

Cycle Sorting - a sorting algorithm focussed specifically on read write ops.

    
    <code>#!/bin/python
    """
    Cycle Sort -
    """
    def cycleSort(array):
    writes = 0
    array_length = len(array)
    for x in range(0, array_length - 1):
    print array
    item = array[x]
    # Find where to put the item.
    pos = x
    for i in range(x + 1, array_length):
    if array[i] < item:
    pos += 1
    # If the item is already there, go to next item.
    if pos == x:
    continue
    # Otherwise, put the item there or right after any duplicates.
    while item == array[pos]:
    pos += 1
    print " Exchange b/w", item, array[pos]
    array[pos], item = item, array[pos]
    print " Exchange ", array
    writes += 1
    # Rotate the rest of the cycle.
    while pos != x:
    pos = x
    for i in range(x + 1, array_length - 1):
    if array[i] < item: pos += 1 # Put the item there or right after any duplicates. while item == array[pos]: pos += 1 print " Exchange b/w", item, array[pos] array[pos], item = item, array[pos] print " Exchange ", array writes += 1 print "Total no.of write ops : %i " % writes >>> cycleSort([2, 1, 0])
    [2, 1, 0]
    Exchange b/w 2 0
    Exchange [2, 1, 2]
    Exchange b/w 0 2
    Exchange [0, 1, 2]
    [0, 1, 2]
    Total no.of write ops : 2
    >>> cycleSort([2, 1, 0, 4])
    [2, 1, 0, 4]
    Exchange b/w 2 0
    Exchange [2, 1, 2, 4]
    Exchange b/w 0 2
    Exchange [0, 1, 2, 4]
    [0, 1, 2, 4]
    [0, 1, 2, 4]
    Total no.of write ops : 2
    >>> cycleSort([2, 1, 0, 4, 3])
    [2, 1, 0, 4, 3]
    Exchange b/w 2 0
    Exchange [2, 1, 2, 4, 3]
    Exchange b/w 0 2
    Exchange [0, 1, 2, 4, 3]
    [0, 1, 2, 4, 3]
    [0, 1, 2, 4, 3]
    [0, 1, 2, 4, 3]
    Exchange b/w 4 3
    Exchange [0, 1, 2, 4, 4]
    Exchange b/w 3 4
    Exchange [0, 1, 2, 3, 4]
    Total no.of write ops : 4
    >>>
    </code>


How we do it?
1. First go with simple loop over array.
2. say x is the loop variable. say y is in the ideal loc of x.
3. First cycle: find x's right place and put it there after taking a copy of y's item.
4. Second cycle: like x, get right place for y and put it back in deck.

For animation on how does cycle sort does, please try [http://sorting.at/](http://sorting.at/). Here your can select algorithm, select type of test case and run it step by step visualization of sorting.
