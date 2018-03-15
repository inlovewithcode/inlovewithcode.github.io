---
author: guidedmissile
comments: true
date: 2015-08-04 13:04:16+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/08/04/knapsnack/
slug: knapsnack
title: 01 Knapsack Algorithm - Recursion - Backtrack - Algo
wordpress_id: 521
categories:
- Python
tags:
- Algorithms
---

Like the robots of Asimov, all recursive algorithms must obey three important laws:



	
  1. A recursive algorithm must have a **base case**.

	
  2. A recursive algorithm must change its state and move toward the base case.

	
  3. A recursive algorithm must call itself, recursively.


Remeber : [http://interactivepython.org/runestone/static/pythonds/Recursion/TheThreeLawsofRecursion.html](http://interactivepython.org/runestone/static/pythonds/Recursion/TheThreeLawsofRecursion.html)

    
    <code>
    max_weight = 15
    max_items = 5
    items = [ 1, 6, 2, 13, 2, 21, 5, 6, 7, 8, 9]
    # #
    def knapsack(current_weight=0, index=0, items_count=0):
        if items_count >= max_items or current_weight > max_weight  :
            # reached items limit
            return current_weight
        if index >= len(items):
            # reached end
            return current_weight
        # either take the item
        take = knapsack(current_weight + items[index], index + 1, items_count + 1)
        # or leave the item
        dont_take = knapsack(current_weight, index + 1, items_count)
        temp = [x for x in [current_weight, take, dont_take] if x <= max_weight]
        return max(temp)
    ##
    print knapsack()
    </code>
    
