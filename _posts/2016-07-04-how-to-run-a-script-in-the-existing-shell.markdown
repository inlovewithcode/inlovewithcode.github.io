---
author: guidedmissile
comments: true
date: 2016-07-04 08:49:41+00:00
excerpt: A quick shortcut for setting local settings for python virtualenv.
layout: post
link: https://inlovewithcode.wordpress.com/2016/07/04/how-to-run-a-script-in-the-existing-shell/
slug: how-to-run-a-script-in-the-existing-shell
title: How to run a script in the existing shell
wordpress_id: 1244
categories:
- Linux Scripting
- Python
- Unix
tags:
- Shell Scripting
- virtualenv
---

In this post, we will answer following questions.

How to run a script in existing shell? or
How to load variables in a script to current(user) shell? or
How to easily load variables into start python virtualenv?




<blockquote>**Why should you learn this?**

It's not always necessary but, sometimes when we are working on multiple projects, it would be wise to define all your environmental variables in once place and use them when required. Of course, you can define them in you .bash profile or anything other profile you are using but think again how good it is to define in your .bash shell? You will overload your shell as well as other people who want use that code later, will also the do same.

Loading variables all with in your shell profiles will again effect your other projects. For my case, I have Python and Anaconda. Anaconda, comes with its own python setup and packages set. Now when I load python, anaconda python loads slowly.

So I follow, following the tradition of setting up an env_settings.sh files to help me. Just because I do, I can't & I won't ask you follow it. This is post aim to let you know there is an option.</blockquote>




In a Unix terminal, when we try to run a script they run in a different shell and finished the job. For example

    
    #!/bin/bash
    # author = msampathkumar
    # purpose = to import settings for local python, pip & virtualenv
    export PATH="/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin"
    source env/bin/activate
    clear


This script is to load my local variables for the application and activate its respective virtual environment. Unfortunately, when I run it with below command it does not give the desired output.

    
    SDS-bash3.2$ sh settings.sh
    SDS-bash3.2$


In such cases, we can use the following method.

    
    SDS-bash3.2$ <strong>. ./settings.sh</strong>
    (env)SDS-bash3.2$


Source:http://unix.stackexchange.com/questions/102838/run-script-in-current-shell-without-before-command
