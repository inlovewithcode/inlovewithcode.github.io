---
author: guidedmissile
comments: true
date: 2015-08-03 09:53:40+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/08/03/python-memorization-with-example/
slug: python-memorization-with-example
title: Python Memorization with Example
wordpress_id: 501
categories:
- Python
tags:
- Memorisation
---

Here we have an example of memorization where our python code will remembers the valuable computations of a function helping in fetching results faster.

Here we have a class - structures where we define our memorize object for remembering our computational values and two function where we do real -is prime- checking for a given list of numbers.

    
    class memoize:
        """ encapsulate the caching of the results """
        def __init__(self, fn):
            self.fn = fn
            self.memo = {}
        def __call__(self, *args):
            if args not in self.memo:
                self.memo[args] = self.fn(*args)
            return self.memo[args]
    
    # remembers what we learnt
    @memoize
    def isprime(num):
        '''checks if number is prime
    
        return type : boolean'''
        if num < 2:
            return False
        if num in [1, 2]:
            return True
        else:
            # check_till - checks till we reach square-root of n.
            check_till = int(num ** 0.5) + 1
            # xrange - fetch number as when required
            # xrange - starts with 3, check for only odd number
            if num % 2 == 0:
                return False
            for div in xrange(3,check_till, 2):
                if num % div == 0:
                    return False
            return True
    
    
    def findPrimes(items):
        """
        returns a list of primes number in given list
        """
        return [ x for x in items if isprime(x)]
    


Notable optimizations:



	
  1. **Memorization** : Saves lot of time by remembering already computed values.

	
  2. **Optimized Division**: We are only checking if number is divisible by 2 and other odd numbers. Checking goes only untill we reach square root of a number.

	
  3. **XRANGE**: Faster than usual "range" as xrange is optimised using c-code(internal python features).


