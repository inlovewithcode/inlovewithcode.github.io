---
author: guidedmissile
comments: true
date: 2013-11-24 14:01:13+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/few-important-tips/
slug: few-important-tips
title: Bash Tips
wordpress_id: 48
categories:
- Linux Scripting
- Unix
tags:
- Bash
- Shell Scripting
---

### Tips:



    
    ` # command substitution
    \ # escape [backslash]. A quoting mechanism for single characters
    / # file path separator
    : # true or do nothing
    ? # test operator
    ${} # parameter substitution
    $? # exit status variable
    $$ # process id variable




##### Example:



    
    :${username=`whoami`}
