---
author: guidedmissile
comments: true
date: 2013-11-24 06:37:14+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/python-setting-command-line-arguments/
slug: python-setting-command-line-arguments
title: Python Setting Command Line Arguments
wordpress_id: 4
categories:
- Python
---

# Example for setting command line arguments

    
    from optparse import OptionParser
    parser = OptionParser()
    parser.add_option("-f", "--filename", dest="filename", help="upload one FILE", metavar="FILE")
    
    (options, args)  =  parser.parse_args()
    input_filename  =  [str(options.filename)]
    print 'Filename provided as input is', input_filename


# How to provide command line input is
# python  -f  sample_file
