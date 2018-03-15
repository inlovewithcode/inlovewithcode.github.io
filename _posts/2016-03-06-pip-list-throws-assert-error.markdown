---
author: guidedmissile
comments: false
date: 2016-03-06 11:40:31+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2016/03/06/pip-list-throws-assert-error/
slug: pip-list-throws-assert-error
title: pip list throws assert error
wordpress_id: 869
categories:
- Python
---

`
Exception:
Traceback (most recent call last):
File "/Users/sampathkumarm/tensorflow/lib/python2.7/site-packages/pip/basecommand.py", line 134, in main
status = self.run(options, args)
File "/Users/sampathkumarm/tensorflow/lib/python2.7/site-packages/pip/commands/list.py", line 80, in run
self.run_listing(options)
File "/Users/sampathkumarm/tensorflow/lib/python2.7/site-packages/pip/commands/list.py", line 127, in run_listing
self.output_package_listing(installed_packages)
File "/Users/sampathkumarm/tensorflow/lib/python2.7/site-packages/pip/commands/list.py", line 136, in output_package_listing
if dist_is_editable(dist):
File "/Users/sampathkumarm/tensorflow/lib/python2.7/site-packages/pip/util.py", line 347, in dist_is_editable
req = FrozenRequirement.from_dist(dist, [])
File "/Users/sampathkumarm/tensorflow/lib/python2.7/site-packages/pip/__init__.py", line 195, in from_dist
**assert len(specs) == 1 and specs[0][0] == '=='**
** AssertionError**`

Storing complete log in /Users/sampathkumarm/.pip/pip.log



_To Fix - edit the existing code as below. Existing code will try to check spec[0][0] is having value as '=='. But I found out that **python-dateutils** has '===' in specs which is why my **pip list** is failing. So, to compensate that - little hack._

`
(tensorflow)bash-3.2$ vi +194 /Users/sampathkumarm/tensorflow/lib/python2.7/site-packages/pip/__init__.py`
Edit line 194 as of pip/__init__.py show in your error code as below
`assert len(specs) == 1 and specs[0][0].startswith('==')
```
