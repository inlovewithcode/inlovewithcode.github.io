---
author: guidedmissile
comments: true
date: 2014-01-30 08:35:33+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2014/01/30/short-notes-on-python-pep8-style-guide/
slug: short-notes-on-python-pep8-style-guide
title: Short Notes on Python PEP8 Style Guide
wordpress_id: 136
categories:
- Python
---

Aim of this PEP 8 Style Guidelines is to improve readability of code. One of Guido's key insights is that code is read much more often than it is written.





## **Code layout**


**Indentation :** 4 spaces are preferred.

Examples :

    
    my_list = [
        1, 2, 3,
        4, 5, 6,
        ]
    result = some_function_that_takes_arguments(
        'a', 'b', 'c',
        'd', 'e', 'f',
        )
    # Aligned with opening delimiter
    foo = long_function_name(var_one, var_two,
                             var_three, var_four)
    
    # More indentation included to distinguish this from the rest.
    def long_function_name(
            var_one, var_two, var_three,
            var_four):
        print(var_one)
    <b style="font-family:Georgia, 'Times New Roman', 'Bitstream Charter', Times, serif;font-size:14px;line-height:1.5em;">Tabs or Spaces :</b><span style="font-family:Georgia, 'Times New Roman', 'Bitstream Charter', Times, serif;font-size:14px;line-height:1.5em;"> Spaces are the preferred indentation method.</span>


**Tip:** When invoking the Python 2 command line interpreter with the -t option, it issues warnings about code that illegally mixes tabs and spaces. When using -tt these warnings become errors. These options are highly recommended!

**Maximum Line Length** :

Limit all lines to a maximum of 79 characters

For Docstrings or comments, the line length should be limited to 72 characters.

    
    with open('/path/to/some/file/you/want/to/read') as file_1, \ # <b>Backslash to shorten line</b>
    
        open('/path/to/some/file/being/written', 'w') as file_2:
    
        file_2.write(file_1.read())


Make sure to indent the continued line appropriately. The preferred place to break around a binary operator is _after_ the operator, not before it. Some examples:
class Rectangle(Blob):

    
    class Rectangle(Blob):
    
        def __init__(self, width, height,
                     color='black', emphasis=None, highlight=0):
            if (width == 0 and height == 0 and
                    color == 'red' and emphasis == 'strong' or
                    highlight > 100):
                raise ValueError("sorry, you lose")
            if width == 0 and height == 0 and (color == 'red' or
                                               emphasis is None):
                raise ValueError("I don't think so -- values are %s, %s" %
                                 (width, height))
            Blob.__init__(self, width, height,
                          color, emphasis, highlight)


**Blank Lines:**



	
  * For Top level functions, classes : 2 Lines

	
  * Method def inside class : 1 Line

	
  * To to indicate logical sections in code : 1 Line


**Source File Encoding : **UTF-8 (or ASCII in Python 2)

**Imports :** Imports should usually be on separate lines

Imports should be grouped in the following order:



	
  1. standard library imports

	
  2. related third-party imports

	
  3. local application/library specific imports


You should put a blank line between each group of imports.

Example:

    
    import os
    import sys
    
    from subprocess import Popen, PIPE


**Comments:**

Keep it Simple, Short & Sweet(KISS) and **explain  only what it does** in simple, in complete sentence. Always make a priority of keeping the comments up-to-date when the code changes!

Comments are costly & use them only when need.

**Naming Conventions:**



	
  1. Avoid names with letters I,O,L

	
  2. Module names should be all-lowercase, short.

	
  3. Class names should normally use the CapWords convention

	
  4. Global Variable Names - begin with  underscore("-").

	
  5. Function Names – lower case, underscore

	
  6. Function and method Args: As Default use, self – for functions and cls – for classes

	
  7. Constants – All uppercase “MAX_OVERFLOW”

	
  8. For exceptions handling explicitly define error expected ! Example "except ImportError:" instead of "except:"


_Source Link : http://www.python.org/dev/peps/pep-0008/_
