---
author: guidedmissile
comments: true
date: 2014-10-01 10:41:30+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2014/10/01/python-workshop/
slug: python-workshop
title: Python workshop for non programmers - April 4th, 2014
wordpress_id: 190
categories:
- Python
tags:
- Workshop
---

**Introduction**

Python is strongly typed (i.e. types are enforced), dynamically, implicitly typed (i.e. you don't have to declare variables), case-sensitive (i.e. var and VAR are two different variables) and object-oriented (i.e. everything is an object).

**Getting Help**

Help in Python is always available right in the interpreter. If you want to know how an object works, all you have to do is call help(<object>)! Also useful are dir(), which shows you all the object's methods, and <object>.__doc__, which shows you its documentation string:

    
    >>> a = 5
    >>> help(a)
    Help on int object:
    (etc)
    
    >>> dir(a)
    ['__abs__', '__add__', '__doc__', ...]
    
    >>> a.__doc__
    Help on int object:
    (etc)


**Syntax**

Python has no mandatory statement termination characters and blocks are specified by indentation. Indent to begin a block, indent to end one. Statements that expect an indentation level end in a colon (:). Comments start with the pound (#) sign and are single-line, multi-line strings are used for multi-line comments. Values are assigned (in fact, objects are bound to names) with the _equals_ sign ("="), and equality testing is done using two _equals_ signs ("=="). You can increment/decrement values using the += and -= operators respectively by the right-hand amount. This works on many data types, strings included. You can also use multiple variables on one line. For example:

    
    >>> 
    >>> myvar = 2
    >>> myvar
    2
    >>> print myvar
    2
    >>> myvar = 1
    >>> myvar += 5
    >>> print myvar
    6
    >>> mystring = "hello world"
    >>> print mystring
    hello world
    >>> 
    >>> mystring = ''' This is a multi-line data string starting
    with a triple single quote and ending with another
    triple quote'''
    >>>


<!-- more -->

**Data types**

The data structures available in python are lists, tuples and dictionaries. Lists are like one-dimensional arrays (but you can also have lists of other lists), dictionaries are associative arrays (a.k.a. hash tables) and tuples are immutable one-dimensional arrays (Python "arrays" can be of any type, so you can mix e.g. integers, strings, etc in lists/dictionaries/tuples). The index of the first item in all array types is 0. Negative numbers count from the end towards the beginning, -1 is the last item. Variables can point to functions. The usage is as follows:

    
    >>> sample = [1, ["another", "list"], ("a", "tuple")]
    >>> sample
    [1, ["another", "list"], ("a", "tuple")]
    >>>
    >>> mylist = ["List item 1", 2, 3.14]
    >>> mylist[0] = "List item 1 again" # We're changing the item.
    >>> mylist[-1] = 3.21 # Here, we refer to the last item.
    >>> mydict = {"Key 1": "Value 1", 2: 3, "pi": 3.14}
    >>> mydict["pi"] = 3.15 # This is how you change dictionary values.
    >>> mytuple = (1, 2, 3)
    >>> myfunction = len
    >>> print myfunction(mylist)
    3


You can access array ranges using a colon (:). Leaving the start index empty assumes the first item, leaving the end index assumes the last item. Negative indexes count from the last item backwards (thus -1 is the last item) like so:

    
    >>> mylist = ["List item 1", 2, 3.14]
    >>> print mylist[:]
    ['List item 1', 2, 3.1400000000000001]
    >>> print mylist[0:2]
    ['List item 1', 2]
    >>> print mylist[-3:-1]
    ['List item 1', 2]
    >>> print mylist[1:]
    [2, 3.14]
    
    # Adding a third parameter, "step" will have Python step in
    # N item increments, rather than 1.
    # E.g., this will return the first item, then go to the third and
    # return that (so, items 0 and 2 in 0-indexing).
    
    >>> print mylist[::2]
    ['List item 1', 3.14]
    
    


<!-- more -->

**Strings**

Its strings can use either single or double quotation marks, and you can have quotation marks of one kind inside a string that uses the other kind (i.e. "He said 'hello'." is valid). Multi Line strings are enclosed in _triple double (or single) quotes_ ("""). Python supports Unicode out of the box, using the syntax u"This is a Unicode string". To fill a string with values, you use the % (modulo) operator and a tuple. Each %s gets replaced with an item from the tuple, left to right, and you can also use dictionary substitutions, like so:

    
     >>> mystring = "hello world"
    >>> print mystring
    hello world
    >>> 
    >>> mystring = ''' This is a multi-line data string starting
    with a triple single quote and ending with another
    triple quote'''
    
    >>> 
    >>>print "Name: %s\
    Number: %s\
    String: %s" % ('hello', 3, "---")
    
    Name: hello
    Number: 3
    String: ---


**Flow control statements**

Flow control statements are if, for, and while. There is no select; instead, use if. Use for to enumerate through members of a list. To obtain a list of numbers, use range().

    
    >>> # This is a comment
    >>> file_sizes = [ 12, 5, 1, 2, 12, 45, 14, 90, 46, 57, 65, 90 ]
    >>> 
    >>> # We are creating a checking loop which tell if \
    any file size more than 20 as Amber and if its more \
    than 60 as Red else Green
    >>> 
    >>> for each in file_sizes:
     if each < 20:
     print "Green"
     else if each < 60:
     print "Amber"
     else
     print "Red"
    ...
    (etc, etc)


<!-- more -->

**Functions**

Functions are declared with the "def" keyword. Optional arguments are set in the function declaration after the mandatory arguments by being assigned a default value. For named arguments, the name of the argument is assigned a value. Functions can return a tuple (and using tuple unpacking you can effectively return multiple values).

    
    >>>def check_filesize(file_sizes):
    '''
    This function is used to check if file sizes.
    If size is < 20 reported as Green,
    if its < 40 and > 20 its Amber,
    if > 40 as Red
    '''
     for each in file_sizes:
     if each < 20:
     print "Green"
     else if each < 60:
     print "Amber"
     else
     print "Red"







