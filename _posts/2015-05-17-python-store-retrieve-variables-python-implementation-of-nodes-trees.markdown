---
author: guidedmissile
comments: true
date: 2015-05-17 19:52:31+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/05/17/python-store-retrieve-variables-python-implementation-of-nodes-trees/
slug: python-store-retrieve-variables-python-implementation-of-nodes-trees
title: Store Variables - Retrieve Variables in Python + Python Implementation of Nodes
  & Trees
wordpress_id: 289
categories:
- Python
tags:
- Trees
---

# Store Variables - Retrieve Variables



    
    # Store
    >>> import cPickle
    >>> sam = range(4)
    >>> cPickle.dump(sam, open ( "sam.pkl" , "w" ))
    
    # Revive
    >>> sam = cPickle.load(open ( "sam.pkl"))
    >>>




# Implementation of Nodes



    
    class Node:
     def __init__(self, value, next=None):
     self.value = value
     self.next = next
    You construct a list by specifying all the nodes:
    >>> L = Node("a", Node("b", Node("c", Node("d"))))
    >>> L.next.next.value
    'c'




# Implementation of Tree



    
    class Tree:
     def __init__(self, left, right):
     self.left = left
     self.right = right
    
    You can use the Tree class like this:
    >>> t = Tree(Tree("a", "b"), Tree("c", "d"))
    >>> t.right.left
    'c'




# Implementation of Multiway Tree Class



    
    class Tree:
     def __init__(self, kids, next=None):
     self.kids = self.val = kids
     self.next = next
    The separate val attribute here is just to have a more descriptive name when supplying a value
    (such as 'c') instead of a child node. Feel free to adjust this as you want, of course. Here’s an example of
    how you can access this structure:
    >>> t = Tree(Tree("a", Tree("b", Tree("c", Tree("d")))))
    >>> t.kids.next.next.val
    'c'




# THE BUNCH PATTERN


When prototyping (or even finalizing) data structures such as trees, it can be useful to have a flexible class
that will allow you to specify arbitrary attributes in the constructor. In these cases, the “Bunch” pattern
(named by Alex Martelli in the Python Cookbook) can come in handy. There are many ways of
implementing it, but the gist of it is the following:

    
    class Bunch(dict):
     def __init__(self, *args, **kwds):
     super(Bunch, self).__init__(*args, **kwds)
     self.__dict__ = self


There are several useful aspects to this pattern. First, it lets you create and set arbitrary attributes by
supplying them as command-line arguments:

    
    >>> x = Bunch(name="Jayne Cobb", position="Public Relations")
    >>> x.name
    'Jayne Cobb'


Second, by subclassing dict, you get lots of functionality for free, such as iterating over the keys/attributes
or easily checking whether an attribute is present. Here’s an example:

    
    >>> T = Bunch
    >>> t = T(left=T(left="a", right="b"), right=T(left="c"))
    >>> t.left
    {'right': 'b', 'left': 'a'}
    >>> t.left.right
    'b'
    >>> t['left']['right']
    'b'
    >>> "left" in t.right
    True
    >>> "right" in t.right
    False


This pattern isn’t useful only when building trees, of course. You could use it for any situation where you’d
want a flexible object whose attributes you could set in the constructor.
