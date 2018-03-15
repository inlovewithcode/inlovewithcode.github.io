---
author: guidedmissile
comments: true
date: 2017-08-05 18:52:49+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2017/08/06/find-the-largest-island-problem/
slug: find-the-largest-island-problem
title: Find the largest Island - Problem
wordpress_id: 2405
categories:
- Python
---


    import numpy as np
    import pandas as pd
    
    np.random.seed(42)
    
    MAX_LEN = 5
    
    def recursive_update(x, y):
        """Recursively updates the neightbouring element to 0 and resturn collected count by udating."""
        global data
        if x  MAX_LEN and y  MAX_LEN:
            # invalid location
            return 0
        count = 0
        if data[x, y] == 1:
            data[x, y] = 0
            count = 1
            if x + 1  0:
                count += recursive_update(x - 1, y)
            if y > 0:
                count += recursive_update(x, y - 1)
            if y + 1  .5)
    
    print(data)
    
    for row in range(len(data)):
        for col in range(len(data[0])):
            score = recursive_update(row, col) 
            if score:
                print((score, data))
    
