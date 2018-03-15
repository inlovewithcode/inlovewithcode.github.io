---
author: guidedmissile
comments: true
date: 2016-10-14 05:26:51+00:00
excerpt: 'How to troubleshoot issue of installing python pygame in Mac.


  Keywords: pygame, anaconda, libpng.dylib'
layout: post
link: https://inlovewithcode.wordpress.com/2016/10/14/macbook-python-pygame-anaconda-issues/
slug: macbook-python-pygame-anaconda-issues
title: MacBook Python Pygame Anaconda - issues
wordpress_id: 1428
categories:
- Python
---

This post is to help you troubleshoot some issue you might find while installing **PYGAME**.

Before we start, I use Mac OS  and Python 2.7.11 |Anaconda custom (x86_64)

    
    SDS-bash3.2$ conda --version
    conda 4.2.9
    SDS-bash3.2$ which anaconda
    /Users/sampathkumarm/anaconda/bin/anaconda
    SDS-bash3.2$ anaconda --version
    anaconda Command line client (version 1.4.0)


Note: My bash prompt looks like this

    
    SDS-bash3.2$




## How did I come to know these Pygame installation errors?


As a part of my smart car project completion, we are required to install Pygame. If you are also doing similar work, I would recommend following steps

Step1: Update number of trails runs to 2 in agent.py

Step2: run agent.py

    
    SDS-bash3.2$ python agent.py > log



    
    SDS-bash3.2$ head log


In case no error message are found are seen in the log then it's good. You should also get **Pygame UI** for simulation if there are no error.

Step3:  In case you see errors in the log. Try to install Pygame using anaconda

    
    SDS-bash3.2$ conda install pygame


As a part project completion, you need Pygame. So while installing Pygame using conda I had this following error

    
    Error: <em><strong>from </strong></em>pygame<em><strong>.base import * ImportError: </strong></em>dlopen
    .....
    ...SDL Error - missing/usr/local/lib/libSDL-1.2.0.dylib...
    ....




##### 




##### **Pygame installation - First problem - SDL Error - missing/**usr**/local/lib/libSDL-1.2.0.dylib**


From the error messages what I understood is SDL related one file is missing (/usr/local/lib/libSDL-1.2.0.dylib).  As I searched about I came to know that it is [Simple Media Direct Layer](http://www.libsdl.org/index.php)  and it is a cross-platform development library designed to provide low level access to audio, keyboard, mouse, joystick, and graphics hardware via OpenGL and Direct3D

Here is the solution that worked for me

    
    SDS-bash3.2$ pip install pygame




Checking if Pygame installed

    
    SDS-bash3.2$ <strong>python</strong>
    Python 2.7.11 |Anaconda custom (x86_64)| (default, Dec 6 2015, 18:57:58)
    [GCC 4.2.1 (Apple Inc. build 5577)] on darwin
    Type "help", "copyright", "credits" or "license" for more information.
    Anaconda is brought to you by Continuum Analytics.
    Please check out: http://continuum.io/thanks and https://anaconda.org
    >>> import pygame
    >>>


Pygame is imported !! Yahoooooooo :)




##### **Pygame installation - Second problem -[Pygame libpng]**


While working with Pygame I found that it is not able to read images and was throwing error like libpng** is not able to read image.**

    
    pygame.error: Failed loading libpng.dylib: dlopen(libpng.dylib, 2): image not found




Here is how I fixed/installed it.

    
    SDS-bash3.2$ <strong>brew install libpng</strong>
    ==> Downloading https://homebrew.bintray.com/bottles/libpng-1.6.19.mavericks.bottle.tar.gz
    ######################################################################## 100.0%
    ==> Pouring libpng-1.6.19.mavericks.bottle.tar.gz
    🍺 /usr/local/Cellar/libpng/1.6.19: 17 files, 1.3M




First time when I tried above command, I was having lots of file path permission. Lots of brew folders are having permission for root and I did not know. So after random browsing, I found this command to try.

    
    SDS-bash3.2$ <strong>brew doctor</strong>


This will tell you all possible issues or reasons if you could not install using brew.

If you see any file path permission issue please fix them and once no more files permission issue are there then proceed to installing libpng.

Wise it would, if you don't try to fix every problem that brew doctor shows.

References:



	
  * [http://stackoverflow.com/questions/34907017/homebrew-wont-brew-any-more](http://stackoverflow.com/questions/34907017/homebrew-wont-brew-any-more)

	
  * [http://www.libsdl.org/index.php](http://www.libsdl.org/index.php)

	
  * [https://discussions.udacity.com/t/pygame-is-no-response/180419/31](https://discussions.udacity.com/t/pygame-is-no-response/180419/31)




Hope this helps!
