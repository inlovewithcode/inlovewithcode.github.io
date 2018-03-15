---
author: guidedmissile
comments: false
date: 2017-03-29 06:10:12+00:00
layout: page
link: https://inlovewithcode.wordpress.com/gnu-make/
slug: gnu-make
title: GNU MAKE
wordpress_id: 1787
---

## make or how to create a makefile



make tool or make file is a simple rule based system to help developers/admins to do repetitive jobs. Here is a basic format of how a make file looks like.

How does a make_file syntax looks like?

[code lang=text]
# syntax of makefile
<rule01>:
<tab/tab_space><command1>

<rule02>:<track_file1> <track_file2>
<tab/tab_space><command2>

<rule03>:<track_file1> <track_file2>
<tab/tab_space><command1>\
<tab/tab_space><command2>
[/code]

How do you run a make command?

[code lang=text]
bash-3.2$ date
Tue Mar 22 21:56:16 IST 2015
bash-3.2$  make rule01
[/code]

Few rules for using this rule based system:





  * File name can be `Makefile` or `makefile`


  * File should in the location where you want to execute make commands


  * with no arguments, make executes the first rule in the file.


  * By putting the list of files on which the command depends on the first line after the ":", make knows that rule needs to be executed if any of those files change.(Like a Trigger)


  * use only tabs for formatting code.


  * make expects executable code is in one line but for convenience, you can use `\` for increasing its scope.



Here is a crazy example/sample makefile for some special people

[code lang=text]
SDS-bash3.2$ ls -l Makefile
-rw-r--r--  1 sampathm  wheel  253 Mar 29 11:36 Makefile
SDS-bash3.2$ cat Makefile
#! /usr/bin/make

# Aliases
GREETINGS="hello sam"

# Helper function - default
help:
    echo "InputError:\
    Try: make list"

# list of commands
list:
    echo "make game # does the stuff"\

# command 1
game:
    echo ${GREETINGS}

# command n
clean:
    rm -f *.o
SDS-bash3.2$ make clean
rm -f *.o
SDS-bash3.2$ make # to see default working
echo "InputError:\
    Try: make list"
InputError:Try: make list
SDS-bash3.2$
SDS-bash3.2$ make list
echo "make game # does the stuff"\

make game # does the stuff
SDS-bash3.2$ make clean
rm -f *.o
SDS-bash3.2$
[/code]

You can consider that this is an introduction to start for learning make. Here is another short quick tutorial for make (http://kbroman.org/minimal_make/), where author mention about how to use variable & regular expression and other operations in make_file.

References: http://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/
