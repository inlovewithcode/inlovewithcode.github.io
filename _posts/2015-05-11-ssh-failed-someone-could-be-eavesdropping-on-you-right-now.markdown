---
author: guidedmissile
comments: true
date: 2015-05-11 12:37:51+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/05/11/ssh-failed-someone-could-be-eavesdropping-on-you-right-now/
slug: ssh-failed-someone-could-be-eavesdropping-on-you-right-now
title: SSH Failed - Someone could be eavesdropping on you right now !!
wordpress_id: 275
categories:
- Linux Scripting
- Unix
tags:
- Bash
- Ssh
---

After setting up with SSH, my bash code which has been successfully running for 6 months failed today.

After a little panic time we found the issue,..

    
    ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no user@server1.example.com


I have to set that **StrictHostKeyCheck=no**, if not you will get error as following

    
    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
    @ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! @
    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
    IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
    Someone could be eavesdropping on you right now (man-in-the-middle attack)!
    It is also possible that the RSA host key has just been changed.
    The fingerprint for the RSA key sent by the remote host is
    e1:9b:5c:16:a6:cd:11:10:3a:cd:1b:a2:16:cd:e5:1c.
    Please contact your system administrator.
    Add correct host key in /home/user/.ssh/known_hosts to get rid of this message.
    Offending key in /home/user/.ssh/known_hosts:1
    RSA host key for www.cyberciti.biz has changed and you have requested strict checking.
    Host key verification failed.
    
