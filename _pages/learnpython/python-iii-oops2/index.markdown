---
author: guidedmissile
comments: false
date: 2017-03-31 18:23:46+00:00
layout: page
link: https://inlovewithcode.wordpress.com/learnpython/python-iii-oops2/
slug: python-iii-oops2
title: 'Python II # OOPS - Part 2'
wordpress_id: 1907
---

All the example here may be or may not be connected to each other depending on the need. Be wise & understand where & how you can use this functionality for your need.



## Getter and Setter Method




    
    <code>class Square:
        def __init__(self, height=0, w
    
        # getter
        @property
        def height(self):
            print(“retriving the height”)
            return self.__height
    
        # setter
        @height.setter
        def height(self, value):
            if value.isdigit():
                self.__height = value
            else:
                print(‘InputError: only numerical value pace’)
    </code>



Note: Check the setter and getter method added for Square class





  * Actual value if `height` is stored in another variable called `__height`


  * Keyword `@property` for getter method


  * Keyword `#.setter` for setter method 





## Methods - class methods




    
    <code>@staticmethod
    def whoami():
        print(“awesome”)
    </code>



Class Methods: It does not matter if class is initialised, it just works.

Note:





  * keyword to note is `staticmethod`


  * Inside params there is no `self`





## Magic Method




    
    <code>def __str__(self):
        return “know thyself”, self.__name__, self.health, self.hp
    </code>



Note: This method gives a meaning result when you print this object otherwise you will only see an instance's meta data which you won’t understand.



## Inheritance




    
    <code>class Mammal(Animal):
        def __init__(self, birthType=”born alive”,…):
            Animal.__init(self, birthType, appearance,…._:
            self.__new_features = new_feature
    
        @property
        def new_features():
            return self.__nurseYoung
    
        @new_feature.setter
        def nurseYoung(self, nurseYpung):
            if nurseYoung.isalpha():
                self.__nurseYOung = nurseYOung
            else:
                print “nurseYOung has to be a string”
    </code>



Note: Look at is **init** method





  * We used parentheses in the Class Name as we using inheritance - otherwise not required.


  * This class called its parent class Animal & then does the initialisation using Animal’s **init** and then


  * For extra variables added variable with its custom getter & setter methods





## overriding




    
    <code>    def __str__(self):
            ## appending super’s output &amp; printing a new info
            return super().__str__() + “ and also nurse their young”
    </code>



Note: This method is to call its parent & use its out and then makes its own new with added information.





  * Parent already has that method.





## Function Overload / Operator Overload ==> no. of input variables is not fixed




    
    <code># In Python - type casting setting is Dynamic
    # In Java, C - its static Type Casting
    ##  def sumAll(self, a_int, b_int, c_int)
    ##  def sumAll(self, a_int, b_int, c_str)
    ##  def sumAll(self, a_int, b_str, c_str)
    
    def sumAll(self, *args):
        sum = 0
        for i in args:
            sum += int(i)
        return sum
    </code>



Note: This method works for any number of inputs number* whether given as number or strings



## polymorphism




    
    <code>def tell_me_whp_are_you(object):
        print(‘my name is’, object.__name__)
    </code>



Note: This method works for any object/instance that has **name** attribute, it does not matter what kind of object it is.



## Magic method (part2) (Already shown once above for **str**)




    
    <code>def __add__(vector1, vector2):
        vector1.x += vector2.x
        vector1.y += vector2.y
        vector1.z += vector2.z
        vector2 = vector1 # repoint &amp; del vector2
        return vector1
    </code>



Note: Like **init**, this **add** can help you create basic functions like add, sub, multiplayer, div, mod-modulus.





  * [Classes, Variables/Attributes, Function/Methods, Getter/Property, Setter] (https://www.youtube.com/watch?v=1AGyBuVCTeE)


  * [Inheritance, Magic Function, Overriding, Function Overloading, polymorphism, magic methods] (https://www.youtube.com/watch?v=d8kCdLCi6Lk)


