---
author: guidedmissile
comments: true
date: 2013-11-24 14:05:40+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/root-user-checking/
slug: root-user-checking
title: Root User Checking
wordpress_id: 50
categories:
- Linux Scripting
---

Root user controls checking

    
    ROOT_UID=0 # Only users with $UID 0 have root privileges.
    
    if [ "$UID" -ne "$ROOT_UID" ]
    then
    echo "Must be root to run this script."
    exit $E_NOTROOT
    fi
