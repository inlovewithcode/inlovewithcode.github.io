---
author: guidedmissile
comments: true
date: 2015-05-17 19:01:07+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/05/17/how-to-create-a-junk-file-for-testing-speed-transfers/
slug: how-to-create-a-junk-file-for-testing-speed-transfers
title: How to create a junk file for testing speed-transfers?
wordpress_id: 279
categories:
- Linux Scripting
- Unix
tags:
- Bash
---

Creating a test file - 10MB dummy file
# dd if=/dev/zero of=dummu.file bs=1024 count=0 seek=$[1024*10]

PKG_MIN_SIZE=400k
MAIN_FILE=dummy.file

split -b $PKG_MIN_SIZE $MAIN_FILE segment
## collecting list of all new segment - filenames
