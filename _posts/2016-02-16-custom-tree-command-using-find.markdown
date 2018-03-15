---
author: guidedmissile
comments: false
date: 2016-02-16 05:17:01+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2016/02/16/custom-tree-command-using-find/
slug: custom-tree-command-using-find
title: custom tree command using find
wordpress_id: 832
categories:
- Linux Scripting
- Unix
---

You can added the following to ~/.bash_profile for use in Terminal.app. Some comments are included to help remember how find is being used.

    
    <code>##########
    ## tree ##
    ##########
    ## example ...
    #|____Cycles
    #| |____.DS_Store
    #| |____CyclesCards.json
    #| |____Carbon
    #| | |____Carbon.json
    # alternate: alias tree='find . -print | sed -e "s;[^/]*/;|____;g;s;____|; |;g"'
    # use$ tree ; tree . ; tree [some-folder-path]
    function tree {
        find ${1:-.} -print | sed -e 's;[^/]*/;|____;g;s;____|; |;g'
    }
    </code>


http://superuser.com/questions/359723/mac-os-x-equivalent-of-the-ubuntu-tree-command

Here is an example, where I am using tree command to see how application is spread across files.

    
    (fab)SDS% tree app | grep -v ".pyc"
    app
    |______init__.py
    |____forms.py
    |____index.py
    |____models.py
    |____static
    | |____css
    | | |____fullcalendar.css
    | | |____fullcalendar.print.css
    | |____img
    | |____js
    | | |____fullcalendar.min.js
    | | |____jquery.min.js
    | | |____moment.min.js
    |____templates
    | |____404.html
    | |____base.html
    | |____help.html
    | |____my_index.html
    | |____new.html
    | |____test.html
    |____translations
    | |____pt
    | | |____LC_MESSAGES
    | | | |____messages.mo
    | | | |____messages.po
    |____views.py
    


Source: http://superuser.com/questions/359723/mac-os-x-equivalent-of-the-ubuntu-tree-command
