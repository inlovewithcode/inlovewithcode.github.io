---
author: guidedmissile
comments: false
date: 2016-01-06 06:36:18+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2016/01/06/python-zip-enumerate-at-atime/
slug: python-zip-enumerate-at-atime
title: 'Python # ZIP & ENUMERATE at atime?'
wordpress_id: 811
categories:
- Python
---

How to ZIP and ENUMERATE at same time?

    
    def foo():
        a = xrange(1, 15000, 1)
        b = xrange(15000, 1, -1)
        for i, (a, b) in enumerate(zip(a, b,)):
            pass
    


In case if you are about to use zip, enumerate, range - in same go, you can do following which is much faster

    
    def boo():
        a = xrange(1, 15000, 1)
        b = xrange(15000, 1, -1)
        for i, a, b in izip(count(), a, b):
            pass
    


Here is function for testing counting execution time.

    
    def delta(func):
        from time import time
        t1 = time()
        func()
        print "execution time : ", time() - t1, 'Sec(s)'
    


Source : http://www.saltycrane.com/blog/2008/04/how-to-use-pythons-enumerate-and-zip-to/
