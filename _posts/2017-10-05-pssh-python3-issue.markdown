---
author: guidedmissile
comments: true
date: 2017-10-05 18:31:32+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2017/10/06/pssh-python3-issue/
slug: pssh-python3-issue
title: PSSH - Python3 Issue
wordpress_id: 2447
categories:
- Python
---

PSSH - Parallel SSH utility has support upto Python3.

For me, who is using python3.6 had following trouble

[code lang="python"]
SDS-bash3.2$ pssh -version
Traceback (most recent call last):
  File &quot;/Users/sampathm/miniconda3/bin/pssh&quot;, line 26, in &lt;module&gt;
    from psshlib.cli import common_parser, common_defaults
  File &quot;/Users/sampathm/miniconda3/lib/python3.6/site-packages/psshlib/cli.py&quot;, line 9, in &lt;module&gt;
    import version
ModuleNotFoundError: No module named 'version'
[/code]

Due to the version difference in Python3, I guess we don't have this library avail.



### Quick Fix:



Open this file error causing `cli.py` file from above code, and update to following changes



#### change 1



Find below code

[code lang="text"]
import version
[/code]

Change to below

[code lang="text"]
try:
  from version import VERSION
except:
  print('[WARN] Could not import version package in', __file__)
  VERSION=2.3
[/code]



#### change 2



Find below code

[code lang="text"]
    parser = optparse.OptionParser(conflict_handler='resolve',
            version=version.VERSION)
[/code]

Change to below

[code lang="text"]
    parser = optparse.OptionParser(conflict_handler='resolve',
            version=VERSION)
[/code]

Hope you had it working now!
