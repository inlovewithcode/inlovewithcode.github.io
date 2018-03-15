---
author: guidedmissile
comments: true
date: 2015-04-02 07:38:37+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/04/02/why-you-shouldnt-parse-the-output-of-ls/
slug: why-you-shouldnt-parse-the-output-of-ls
title: Why you shouldn't parse the output of ls?
wordpress_id: 259
categories:
- Unix
tags:
- Shell Scripting
---

When people try to use ls to get a list of filenames (either all files, or files that match a glob, or files sorted in some way) things fail disastrously.

If you just want to iterate over all the files in the current directory, use a for loop and a glob:

    
    <code># Bad
    for f in `ls`
    do 
    ...
    done
    # Good!
     for f in *; do
     [[ -e $f ]] || continue
     ...
     done</code>


Consider also using "shopt -s nullglob" so that an empty directory won't give you a literal '*'.

    
    <code># Good! (Bash-only)
     shopt -s nullglob
     for f in *; do
     ...
     done</code>


_Source: http://mywiki.wooledge.org/ParsingLs_
