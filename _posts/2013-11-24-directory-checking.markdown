---
author: guidedmissile
comments: true
date: 2013-11-24 14:10:25+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/directory-checking/
slug: directory-checking
title: Directory Checking
wordpress_id: 52
categories:
- Linux Scripting
- Unix
tags:
- Bash
- Shell Scripting
---

## Directory Listing



    
    cd $LOG_DIR
    if [ `pwd` != "$LOG_DIR" ] # or if [ "$PWD" != "$LOG_DIR" ]
    # Not in /var/log?
    then
    echo "Can't change to $LOG_DIR."
    exit $E_XCD
    fi # Doublecheck if in right directory, before messing with log file.
    




## Another way to do it,.



    
    Another way to do it
    E_XCD=66 # Can't change directory?
    cd /var/log || {
     echo "Cannot change to necessary directory." >&2
     exit $E_XCD;
     }
    
