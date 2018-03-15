---
author: guidedmissile
comments: true
date: 2014-09-15 11:32:37+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2014/09/15/python-embellishments/
slug: python-embellishments
title: Python Embellishments
wordpress_id: 188
categories:
- Python
tags:
- Practice
---

Here are some of Pythonic experts signatures,..

As a junior programmer when I started out, I did find very difficult to understand or use some of these but as I have started learning I find these simple tips are help me to code faster. If you are a fresher, I would suggest learn these 5 - any, all, lambda, filter, lists

    
    # As a jr. this is how I wrote code earlier
    int i,j;
    j = 10;
    while i < j:
       print i
       i = i + 1;
    
    # Today, I am search better one for below
    for i in range(10):
      print i


Tip: 21

    
    def map_example(my_iterable):
     return list(map(lambda x: x + 1, my_iterable))
    
    my_list = [1,2,3,4,5]
    print(map_example(my_list))
    
    def filter_example(my_iterable):
     return list(filter(lambda x: x > 3, my_iterable))
    
    my_list = [1,2,3,4,5,6]
    print(filter_example(my_list))
    
    


Tip: 21

    
    filtered = [x for x in range(1,10) if x % 2==0 ]
    mapped = [f(x) for x in range(1,10) ]
    
    filtered = filter(lambda x: x%2==0, range(1,10))
    mapped = map(f,range(1,10))
    
    


Tip: 21

    
    map(str, collection)
    
    [str(elem) for elem in collection] 
    


Tip: 21

    
    import operator as op
    
    op_map = {
     '$lt': op.lt,
     '$lte': op.le,
     '$gt': op.gt,
     '$gte': op.ge,
     '$ne': op.ne,
     '$eq': op.eq}
    
    if cond_test in ['$eq', '$ne', '$gt', '$gte', '$lt', '$lte']:
     return op_map[cond_test](elem1, elem2):
    return False
    
    


Tip: 21

    
    def test_vaarg(**kwargs):
     for key in kwargs:
     print kwargs[key]
    
    


Tip: 21

    
     Chaining comparison
    
    >>> x = 5
    >>> 1 < x < 10
    True
    >>> 10 < x < 20 
    False
    >>> x < 10 < x*10 < 100
    True
    
    


Tip: 21

    
     enumerate
    
    >>> a = ['a', 'b', 'c', 'd', 'e']
    >>> for index, item in enumerate(a): print index, item
    ...
    0 a
    1 b
    2 c
    3 d
    4 e
    
    


Tip: 21

    
    >>> n = ((a,b) for a in range(0,2) for b in range(4,6))
    >>> n
    <generator object <genexpr> at 0x02086418>
    >>> list(n)
    [(0, 4), (0, 5), (1, 4), (1, 5)]
    
    


Tip: 21

    
     Decorators 
    >>> def print_args(function):
    >>> def wrapper(*args, **kwargs):
    >>> print 'Arguments:', args, kwargs
    >>> return function(*args, **kwargs)
    >>> return wrapper
    
    >>> @print_args
    >>> def write(text):
    >>> print text
    
    >>> write('foo')
    Arguments: ('foo',) {}
    foo
    


Tip: 21

    
    Conditional Assignment
    
    x = 3 if (y == 1) else 2
    
    >>> print("The {foo} is {bar}".format(foo='answer', bar=42))
    
    


Tip: 21

    
    Nested list comprehensions and generator expressions:
    
    [(i,j) for i in range(3) for j in range(i) ] 
    
    


Tip: 21

    
     
    You can easily transpose an array with zip.
    
    a = [(1,2), (3,4), (5,6)]
    zip(*a)
    
    


Tip: 21

    
    hello = "Greaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa Hello " \
     "Word"
    or
    
    hello = ("Greaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa Hello " 
     "Word")
    


Tip: 21

    
    import unittest, textwrap
    
    class XMLTests(unittest.TestCase):
     def test_returned_xml_value(self):
     returned_xml = call_to_function_that_returns_xml()
     expected_value = textwrap.dedent("""\
     
     
     my_content
     
     """)
    
     self.assertEqual(expected_value, returned_xml)
    
    


Tip: 21

    
    if isinstance (number, float) or isinstance (number, int): 
     print "yaay"
    


Tip: 21

    
    > int('10', 0)
    10
    >>> int('0x10', 0)
    16
    >>> int('010', 0) # does not work on Python 3.x
    8
    >>> int('0o10', 0) # Python >=2.6 and Python 3.x
    8
    >>> int('0b10', 0) # Python >=2.6 and Python 3.x
    2
    
    


Source of Information:



	
  * http://www.reddit.com/r/dailyprogrammer/comments/2d957i/weekly_6_python_tips_and_tricks/

	
  * http://stackoverflow.com/questions/101268/hidden-features-of-python

	
  * http://www.secnetix.de/olli/Python/lambda_functions.hawk


