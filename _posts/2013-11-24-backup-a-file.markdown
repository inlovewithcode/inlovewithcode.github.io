---
author: guidedmissile
comments: true
date: 2013-11-24 14:24:43+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/backup-a-file/
slug: backup-a-file
title: Backup a file with date
wordpress_id: 56
categories:
- Linux Scripting
- Unix
tags:
- Bash
---

FILENAME='/var/tmp/test.txt'
    #
    OUTPUT=${FILENAME}$(date +"%Y_%m_%d_%H:%M:%S")
    cp ${FILENAME} ${OUTPUT}
    gzip -9 ${FILENAME} 
    # gzip -d {FILENAME}".gz" # unzip command
