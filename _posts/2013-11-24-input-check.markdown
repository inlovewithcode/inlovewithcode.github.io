---
author: guidedmissile
comments: true
date: 2013-11-24 13:49:11+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/input-check/
slug: input-check
title: Input check
wordpress_id: 44
categories:
- Linux Scripting
tags:
- Bash
- Shell Scripting
---

Test if command line inputs are given or not.

    
    if [ -n "$1" ]
    # Test if command line argument present (non-empty).
    then
    lines=$1
    else
    lines=$LINES # Default, if not specified on command line.
    fi


How to runscript with input is

    
    ./scriptname "InputHere"
