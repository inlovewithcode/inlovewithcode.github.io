---
author: guidedmissile
comments: true
date: 2013-11-24 13:55:51+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/rpm-pre-installation-checking-script/
slug: rpm-pre-installation-checking-script
title: RPM Pre-Installation Checking Script
wordpress_id: 46
categories:
- Linux Scripting
---

This is copied from sources over internet. A good example on how to write a script.

    
    #!/bin/bash
    # rpm−check.sh
    # Queries an rpm file for description, listing, and whether it can be installed.
    # Saves output to a file.
    #
    # This script illustrates using a code block.
    SUCCESS=0
    E_NOARGS=65
    if [ −z "$1" ]
    then
    echo "Usage: `basename $0` rpm−file"
    exit $E_NOARGS
    fi
    {
    echo
    echo "Archive Description:"
    rpm −qpi $1 # Query description.
    echo
    echo "Archive Listing:"
    rpm −qpl $1 # Query listing.
    echo
    rpm −i −−test $1 # Query whether rpm file can be installed.
    if [ "$?" −eq $SUCCESS ]
    then
    echo "$1 can be installed."
    else
    echo "$1 cannot be installed."
    fi
    echo
    } > "$1.test" # Redirects output of everything in block to file.
    echo "Results of rpm test in file $1.test"
    # See rpm man page for explanation of options.
    exit 0



