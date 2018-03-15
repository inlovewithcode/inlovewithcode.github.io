---
author: guidedmissile
comments: false
date: 2015-12-17 08:51:54+00:00
excerpt: explains how to use itertools.izop_longest for packing non uniform lists
  together
layout: post
link: https://inlovewithcode.wordpress.com/2015/12/17/python-zip-non-uniform-lists/
slug: python-zip-non-uniform-lists
title: 'Python # How to zip non uniform lists?'
wordpress_id: 683
categories:
- Python
---

In Python, we generally use ZIP tool for parsing multiple lists at once but if these list sizes are different then that parsing stop at the min length among lists used in ZIP tool.

Here we introducing a new tool where this iZIP tool will parse till last element of lists is used iZIP Tool ( itertools.izip_longest)

Code:

    
    >>> import itertools
    >>> a1=[1,2,3,6,7,9]
    >>> c1=['a','a','c','d']
    >>> b1=[10,20,30,40,50,60]
    >>> d1=[11,12,13,14,15,16,17,18]
    >>> mylist = list(itertools.izip_longest(a1,b1,c1,d1))
    >>> 
    >>> mylist
    [(1, 10, 'a', 11), (2, 20, 'a', 12), (3, 30, 'c', 13), (6, 40, 'd', 14), (7, 50, None, 15), (9, 60, None, 16), (None, None, None, 17), (None, None, None, 18)]
    >>> from pprint import pprint
    >>> 
    >>> 
    >>> pprint(mylist)
    [(1, 10, 'a', 11),
     (2, 20, 'a', 12),
     (3, 30, 'c', 13),
     (6, 40, 'd', 14),
     (7, 50, None, 15),
     (9, 60, None, 16),
     (None, None, None, 17),
     (None, None, None, 18)]
    




``Happy learning :)

Thanks to http://pastebin.com/Tqf26Cvt
