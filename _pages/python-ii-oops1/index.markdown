---
author: guidedmissile
comments: true
date: 2015-06-27 04:38:47+00:00
layout: page
link: https://inlovewithcode.wordpress.com/learnpython/python-ii-oops1/
slug: python-ii-oops1
title: 'Python II # OOPS - Part 1'
wordpress_id: 438
---

#### Classes and methods



**object-oriented language:** A language that provides features, such as user defined classes and inheritance, that facilitate object-oriented programming.
**object-oriented programming:** A style of programming in which data and the operations that manipulate it are organized into classes and methods.
**method:** A function that is defined inside a class definition and is invoked on instances of that class.
**override:** To replace a default. Examples include replacing a default value with a particular argument and replacing a default method by providing a new method with the same name.
**initialization method:** A special method that is invoked automatically when a new object is created and that initializes the object’s attributes.
**operator overloading:** Extending built-in operators (+, -, *, >, >, etc.) so that they work with user-defined types.
**dot product:** An operation defined in linear algebra that multiplies two Points and yields a numeric value.
**scalar multiplication:** An operation defined in linear algebra that multiplies each of the coordinates of a Point by a numeric value.
**polymorphic:** A function that can operate on more than one type. If all the operations in a function can be applied to a type, then the function can be applied to a type.



#### Sample Example of a Class




    
    >>> class game():
        name = '30 seconds race'
        def start_race(self):
            time.sleep(30)
            print 'Time up!!'
    
            
    >>> test = game()
    >>> test.name
    '30 seconds race'
    >>> test.start_race()
    Time up!!
    





#### Sample Example of a Class(part 2)




    
    class Point:
        def __init__(self, x=0, y=0):
            # initialisation method
            self.x = x
            self.y = y
        def __str__(self):
            # output for print function on this class
            return '(%s, %s)' % (self.x, self.y)
    
    
    >>> p = Point(3, 4)
    >>> print p
    (3, 4)
    





#### Sample Example of a Class "operator overloading"(part 2)




    
    class Point:
        # previously defined methods here...
        def __add__(self, other):
            return Point(self.x + other.x, self.y + other.y)
    
    >>> p1 = Point(3, 4)
    >>> p2 = Point(5, 7)
    >>> p3 = p1 + p2
    >>> print p3
    (8, 11)
    



Classes multiplication - magic functions


    
    def __mul__(self, other):
        return self.x * other.x + self.y * other.y
        
    >>> p1 * p1
    (9, 16)
    



Class & Scalar multiplication


    
    def __mul__(self, other):
        return self.x * other.x + self.y * other.y
    
    >>> p1 * 10
    (30, 40)
    





#### How to compare two classes?



To compare the contents of the objects—"deep equality"—we can write a function to check if both are same class and has same attributes

How to check if two variables are point to same information?
we can 'is' for checking if two variable/objects are representing same.


    
    >>> class car():
        pass
    
    >>> a = car()
    >>> b = car()
    >>> a = b # assigning 'b' to 'a'
    >>> a is b
    True
    >>> a == b
    True
    
    
    >>> a = car()
    >>> b = car()
    >>> a is b
    False
    >>> a == b
    False
    >>> 
    





#### How to copy two objects?



Default pkg - copy has
- copy function which does as following

[![copy_copy](https://inlovewithcode.files.wordpress.com/2015/06/copy_copy1.jpg?w=300)](https://inlovewithcode.files.wordpress.com/2015/06/copy_copy1.jpg)




    
  * deep_copy function which we can use for copying(two diff. objs but same* parameter)




    
    >>> import copy
    
    >>> a = car()
    >>> b = car()
    >>> a = copy.copy(b)
    >>> a is b
    False
    >>> a == b
    False
    
