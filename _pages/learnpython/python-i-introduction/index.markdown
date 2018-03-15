---
author: guidedmissile
comments: true
date: 2014-05-26 08:21:23+00:00
excerpt: Python Introduction, Quick Start, Data Types, Loops, Functions, File Operations
layout: page
link: https://inlovewithcode.wordpress.com/learnpython/python-i-introduction/
slug: python-i-introduction
title: Introduction - Quick Start
wordpress_id: 163
---

#### Introduction



Python is a well-designed language with a reasonably clean syntax, a comprehensive standard library, excellent included and third-party documentation, widespread deployment, and the immediacy of a "scripting" style language (ie. no explicit compile step) ([Source](http://programmers.stackexchange.com/questions/5427/why-such-popularity-with-python))

https://imgs.xkcd.com/comics/python.png

Dear reader, we believe you have a fair understanding of what programming language means and little knowledge of how it is. Programming is not just about doing some chit-chat learning, and code some that work & gives a specified output. Like everything - place, object, person,. a programming language has its own beauty. For a while, doing web surfing you may feel beauty is also about speed, while you a search for project & contents, it's about finding more links and more information from multiple sources,. Like in this case, you see beauty can be variable, so does for programming languages as well.

You can browse the application of Python in there in almost everywhere internet - [https://www.python.org/about/apps/](https://www.python.org/about/apps/)

**Few things to know**




    
  1. Python Interactive shell: It’s dynamic, case-sensitive, attractive and simple Style.

    
  2. You don't specifically have to define type of the variables.

    
  3. Variables – Type Checking: In order to know about a variable type you already defined u can use a default function "type"

    
  4. Simple help function.

    
  5. Dir function: To know all about the operations that are available defined about a default function we use "dir" function. dir()



Note: Dear Pythonists, we call python as batteries loaded. It mean, python comes with all basic to great and many more wonderful libraries which are useful to you and help your escape burden to write lots of code. From a calculator program to setting up a small scale database, we have probability one of the best set of open source tools and packages in and around to do almost any kind of jobs.

In python, you will learn all things in a week or two but to be the best you got to beat the best. For that, you need to **learn more about packages** and others which we will learn soon after you finish this page.




    
  6. Python is very stylish. Don’t believe me? Why not try?



In python very imp is coding design - indentation is very important! The Founding father of Python, Guido van Rossum have made a strict rule of this, to make sure that code is more readable. I personally did not like when I started learning about python but during my years of experience in Python, I found that this is my 2nd favorite thing in Python while 1st being Python has a added advantage of C and Java.




    
  7. If you are having py 2.6 or later versions you will be provided a IDLE - Editor for writing `py` script.py is the suffix for py scripts or code files.  .pyc for compiled files; if you are saving a file with .py - once u right-click on it will get option "open with IDLE"



Once you open a script - "Alt + X" for check the py script IDLE.  In shell you have to "import" to run a function defined in script, after syntax check and import - do `dir()` ;





  1. If you have already did `import` once and edited - to import again use `reimport` .



 

**How to put comments in a Python Script?**

There are more than a couple of ways to do this in Python.




    
  * One way is to use `#` keyword, for single line comments.

    
  * Second way is to use triple quote, also known as multiline comments. Here we use (`'''` or `"""` ), 3 continuous quotes - use either single or double, these quotes should be in pairs. One set of quotes to start comments and other set is to end comments.



 

**How to import a script/module/re-import?**

import script/reimport script # syntax check



### Tutorial  Part 1:



Get ready for basic experimentation.

Mathematics


    
    >>> 12 + 12
    >>> 12.0 * 12
    >>> 10000000000000000



Strings


    
    >>> bjorn = "Hello World"
    >>> print bjorn
    >>> dir(bjorn)
    >>> type(bjorn)
    >>>  print “a”,”a”
    >>> print “a” + “a”



Lists


    
    >>> bjorn = []
    >>> bjorn.append('1')



Tuples


    
    >>> tup1 = (1,2,3)
    >>> (x,y,z) = tup1
    >>> print x
    >>> print x,y,z



Dictionary


    
    >>> bjorn = dict()
    >>> dict['sam'] = 'teacher'



IO - operations


    
    >>> data = input(“input data please:”)
    >>> data = raw_input(“input data :”)



Function Declaration


    
    def myPrint(input1):
        print input1
        return 'success'



Loops


    
    for i in range(12):
    print i




    
    for i in range(12):
    print i, # comma is present here




    
    i = 0;
    while i < 12:
    print i
    i = i + 1;
    



Logical Operators


    
    
    “and” “or” “=” “==” “!=” “is” “is not” “not” “”
    





# please checks the data types & method from Wikipedia for more info: doing above operations will help you do some simple operations in py. (WikiLink)



File Operations - writing


    
    fp = open("newfile.py",'w')
    fp.write('This is new file')
    fp.close()
    



File Operations - Reading


    
    fp = open("newfile.py",'r')
    fp.readlines() 
    



This fetches all the data in form of a list of rows.


    
    fp.read()



This fetchall the all the data info file with one go as a single connected string. We can use, instead of “fp.readlines” for reading a file.


    
    fp.close()



http://www.openbookproject.net/thinkcs/python/english2e/
http://imagefriend.com/python-language-comic.shtm
http://www.jeffpalm.com/fox/fox.jpg
