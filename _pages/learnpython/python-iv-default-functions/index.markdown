---
author: guidedmissile
comments: true
date: 2015-07-02 06:34:00+00:00
layout: page
link: https://inlovewithcode.wordpress.com/learnpython/python-iv-default-functions/
slug: python-iv-default-functions
title: 'Python IV # Default Functions'
wordpress_id: 458
---

## Python's Standard Tools/Default Functions



These default function generally are used by almost all experienced Python programmer to make their codes simple & easy to read. Knowing these will also help you save some time and also read other programmers code.

**range**: To generate a list of numbers we use range function.


    
    <code>>>> print(range(5))
    [0, 1, 2, 3, 4]
    </code>



In python3, let us say we have a bit of laziness so we have to do `print(list(range(5)))` instead of just `range(5)` to print. But on the other side of this lazy, we actually gain speed while working in real time.

**lambda**: To define anonymous functions on instinct


    
    <code>>>> f = lambda x : return x*2
    >>> f(2)
    4
    </code>



**map**: To map things like function over a list of objects


    
    <code>>>> f = lambda x : x * 2
    >>> list(map(f, [ 1, 2, 3 ]))
    [ 2, 4, 6]
    </code>



**filter**: Similar to map except, we select items from the list based on a filter function


    
    <code>>>> f = lambda x : x % 2 == 0 # filter funciton for finding odd number
    >>> list(range(12))
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
    >>> list(filter(f, range(12)))
    [2, 4, 6, 8, 10]
    >>>
    </code>



**reduce**: Similar to map except, we take a list apply a function and reduce it to one. In Python3, this function is moved to `functools`. So to use reduce `from functools import reduce` for this job.


    
    <code>>>> f = lambda x, y : x + y
    >>> reduce( f, [ 1, 2, 3 ])
    6
    </code>



**all**: To checks if all values are True or not.


    
    <code>>>> all([True, True, True ]])
    True
    </code>



**any**: To checks if any value is True or Not.


    
    <code>>>> any([True, False, False, False])
    True
    </code>



**zip**: While iterating helps us to take two items at a time.


    
    <code>>>> for x, y in zip ([0, 1, 3], [3, 1, 0]):
    ...     print x, y
    0 3
    1 1
    3 0
    </code>



**sorted**: Similar to sort function list. Here we are using `key` and `reverse` parameters to define criteria of the sort.


    
    <code>>>> sorted([2, 4, 1, 9, 4, 2], key = lambda x: -x, reverse=True)
    [1, 2, 2, 4, 4 9]
    </code>



**hash**: Hashes


    
    <code>>>> hash('hash my name')
    >>> -8636703764421508254
    </code>



**counter**:


    
    <code>from collections import Counter
    x = Counter([1, 1, 12, 12, 21, 21, 21, 12, 122, 21, 21, 2 , 2, 2, 1, 1])
    In [13]: x
    Out[13]: Counter({21: 5, 1: 4, 2: 3, 12: 3, 122: 1})
    </code>



**Multiple Assignment Operator**:


    
    <code>a = b = c = 12 # valid
    a, b = 2, 1 # valid
    </code>





## List Comprehension:



List comprehensions are the simplest and quick forms of generating lists when we need to use multiple operators like filters and mappers.



### Example 1:




    
    <code>>>> f = lambda x : x % 2 == 0 # filter funciton for finding odd number
    >>> list(filter(f, range(12)))
    [0, 2, 4, 6, 8, 10]
    >>>
    >>> # List comprehension
    >>> [x for x in range(12) if x % 2 == 0]
    [0, 2, 4, 6, 8, 10]
    </code>





### Example 2:




    
    <code>>>> list(map(lambda x: x ** 2, filter(lambda x: x % 2, range(12))))
    [1, 9, 25, 49, 81, 121]
    >>>
    >>> [ x ** 2  for x in range(12) if x % 2]
    [1, 9, 25, 49, 81, 121]
    </code>





### Example 3:



We are doing a list comprehension with two lists and also doing a filtering.


    
    <code>>>> [ x * y for x in range(12) for y in range(12) if x == y ]
    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121]
    </code>





## Conditional Assignment




    
    <code>>>> x = 12 if 1 == 1 else 1
    >>> x
    12
    >>> x = 12 if 1 == 11 else 1
    >>> x
    1
    </code>
