---
author: guidedmissile
comments: false
date: 2016-03-06 11:07:16+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2016/03/06/downgrade-python-virtualenv/
slug: downgrade-python-virtualenv
title: Downgrade python virtualenv
wordpress_id: 864
categories:
- Python
---

`
virtualenv.py, line 787, in call_subprocess % (cmd_desc, proc.returncode))
`
In case if you are having a trouble with **python virtualenv ** then try to downgrade your virtualenv version to 1.10 insead of 1.11;

`
sudo easy_install virtualenv==1.10.1
`
