---
author: guidedmissile
comments: true
date: 2013-11-24 06:56:15+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/python-check/
slug: python-check
title: How to Search files in code?
wordpress_id: 7
categories:
- Python
---

Example on how to parse/search for file in a directory

    
    import os
    import re
    
    PATH = '.'       # Current Directory
    PATTERN = '.bak' # Check for if filename contains this pattern
    
    def print_matched_files(path=PATH,pattern=PATTERN):
        ''' 
        prints files in a location
        '''
        count = 1
        print '[=================][Input]'
        print 'File Location',path
        print 'Search pattern provided',pattern
        print '[=================][Printing files ....]'
        files = [f for f in os.listdir(PATH) if re.match(PATTERN, f)]
        for each in files:
            print count,'Filename Name',each
            count = count + 1
        print '[=================][Printing files completed]'
