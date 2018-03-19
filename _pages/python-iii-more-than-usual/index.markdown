---
author: guidedmissile
comments: true
date: 2015-06-29 00:41:09+00:00
layout: page
link: https://inlovewithcode.wordpress.com/learnpython/python-iii-more-than-usual/
slug: python-iii-more-than-usual
title: 'Python III # Real Learning'
wordpress_id: 451
---

#### What can you learn here?


** How present data into easily understandable format? **
Data Formatting 

** How to raise custom exception? **
Exception Handling 

** How can we write linked lists in Python? **
Linked Lists 

** How to implementing stacks with Python lists? **
Stacks 


#### How to format string output data?


Data representation in easily understand manner as important as data. It created a readability for user to work better for example,. output of ls -l, ps -ef in unix os.

In Python, we have "format" mechanisms which we use for formatting data in easily readable format.

    
    >>> def test():
    	out_format = '%-15s%-15s%s' 
        sample_data = [ ('1', '22', '333'), ('111', '22', '3'), ('Tom', 'Dick', 'Harry')]
        # first 15 characters for first column %-15s
        #  next 15 characters for second column
        #  last - no need to format
        # if '-' is present it means, align data left in column space
    	for items in sample_data:
    		print out_format % items
    
    >>> test()
    1              22             333
    111            22             3
    Tom            Dick           Hary
    


**
How to handle floats - formats?
**

    
    >>> "%-20s %12.2f" % ('Server Bios Version', 2.0212)
    'Server Bios Version          2.02'
    >>> "%-20s %12.4f" % ('Server Bios Version', 2.0212)
    'Server Bios Version        2.0212'
    >>> 
    



    
    def report (wages) :
        students = wages.keys()
        students.sort()
        for student in students :
        print "%-20s %12.2f" % (student, wages[student])
    


To test this function, we'll create a small dictionary and print the contents:

    
    >>> wages = {’mary’: 6.23, ’joe’: 5.45, ’joshua’: 4.25}
    >>> report(wages)
    joe             5.45
    joshua          4.25
    mary            6.23
    




#### Gist


Meaning of '%-15s%-15s%s':
# first 15 characters for first column %-15s
# next 15 characters for second column
# last - no need to format
# if '-' is present it means, align data left in column space


#### How to raise custom exception?



    
    >>> def test():
    	x = input()
    	if x == 42:
    		raise ValueError,'input other than 42'
    
    	
    >>> test()
    1212
    >>> 1212
    1212
    >>> test()
    42
    
    Traceback (most recent call last):
      File "<pyshell#96>", line 1, in 
        test()
      File "<pyshell#93>", line 4, in test
        raise ValueError,'input other than 42'
    ValueError: input other than 42
    




#### Linked lists



    
    class Node:
        def __init__(self, cargo=None, next=None):
            self.cargo = cargo
            self.next = next
        def __str__(self):
            return str(self.cargo)
    




#### Implementing stacks with Python lists



    
    class Stack :
        def __init__(self) :
            self.items = []
        def push(self, item) :
            self.items.append(item)
        def pop(self) :
            return self.items.pop()
        def isEmpty(self) :
            return (self.items == [])
    
