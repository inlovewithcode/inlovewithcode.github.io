---
author: guidedmissile
comments: false
date: 2015-12-30 16:45:18+00:00
excerpt: As a part of application development should we maintain virtual env in python
  or use docker in production space?
layout: post
link: https://inlovewithcode.wordpress.com/2015/12/30/python-virtual-env-python-apps-in-production/
slug: python-virtual-env-python-apps-in-production
title: Can I virtual env python-apps in production?
wordpress_id: 800
categories:
- Python
tags:
- Django
---

Can I virtual env python-apps in production?

Upgrading projects are one the special projects to normal. To put what makes it so special is we don’t create a application architecture but we need to understand an existing one and think of ways of improvising it.

**How about running production server in Python Virtual Environment?**
+ You can create multiple instance of python like
++ python2 & python3 with multiple varieties of packages
+ Package interdependencies will be set clear
+ System packages

**Can dockers replace python virtual env?**
Sorry, no.
Virtualenv’s job isn’t just to separate your projects from each other. Its job is also to separate you from the operating system’s Python installation and the installed packages you probably have no idea about. Further reading, you can find at https://hynek.me/articles/virtualenv-lives/.

**Should I use docker or python virtual env?**
You should use both at once, neither replaces the other:

* Do isolate your application server’s OS from its host using Docker/lxc/jails/zones/kvm/VMware/… to one container/vm per application.

* But inside of them also do isolate your Python environment using virtualenv from unexpected surprises in the system site-packages.

Further reading, you can find at https://hynek.me/articles/virtualenv-lives/ .



Overall I see a good advantage in running python application in virtual environment. What's next is up to you now,. godspeed :)
Source:
[https://www.reddit.com/r/Python/comments/2grmnn/virtualenv_on_production/](https://www.reddit.com/r/Python/comments/2grmnn/virtualenv_on_production/)
[https://hynek.me/articles/virtualenv-lives/](https://hynek.me/articles/virtualenv-lives/)
