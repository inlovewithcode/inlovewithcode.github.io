---
author: guidedmissile
comments: false
date: 2016-09-30 11:51:43+00:00
layout: page
link: https://inlovewithcode.wordpress.com/learnpython/python-tools/
slug: python-tools
title: Python Tools
wordpress_id: 1373
---

## Python Installation





	
  * [Anaconda](https://docs.continuum.io/anaconda/install) (python + pip + jupyter notebook + ipython + numpy + scipy + scikit + matplotlib + ... so on)




One cool thing I like in Anaconda is my control to update packages at once. Try below command if you have already installed Anaconda.

    
    conda update


One best part in Anaconda is that it comes with package compatibility management and this reason is why I prefer Anaconda to standard Python Installer. A bit heavy but in long run I feel satisfied.




## Python Virtual Environment





	
  * [Learn Virtual Env](https://inlovewithcode.wordpress.com/2016/06/10/python-virtualenv-tips/)


Virtual Environment provide you a special testing platform like a virtual environment or a virtual box for developing python project where you need to understand and track python pakages that are regularly used.



**If you are fairly new to**** Python, I would not recommend**** these following tools as below are not to help you write code. Below tools are to help you write better code and user documentation.**






## Code-Style/PEP8 Review Tools





	
  * [pep8](https://pypi.python.org/pypi/pep8) (comes as default install for Anaconda)

	
  * [flakes8](https://anaconda.org/anaconda/flake8) (needs custom* install for Anaconda)


For flakes8, if you have sublime please set path settings carefully. Once [sublime path setting](http://www.sublimelinter.com/en/latest/usage.html) is done, you can check for Sublime package manager to install

usage: post installation these packages are available as command line tools in you terminal. I am using MacBook & Anaconda 2.(something).

    
    bash3.2$ pep8 sam.py
    sam.py:46:80: E501 line too long (111 > 79 characters)
    sam.py:49:80: E501 line too long (105 > 79 characters)
    
    bash3.2$ flake8 sam.py
    sam.py:6:1: F401 'time' imported but unused
    sam.py:7:1: F401 're' imported but unused
    sam.py:11:1: F401 'By' imported but unused
    sam.py:12:1: F401 'Keys' imported but unused
    sam.py:13:1: F401 'Select' imported but unused
    sam.py:46:80: E501 line too long (111 > 79 characters)
    sam.py:49:80: E501 line too long (105 > 79 characters)
    sam.py:60:42: F841 local variable 'e' is assigned to but never used
    sam.py:70:43: F841 local variable 'err' is assigned to but never used





## Testing Tools





	
  * doctest

	
  * unittest





## Documentation





	
  * [sphinx](https://anaconda.org/anaconda/sphinx) (needs custom* install in Anaconda)


https://www.youtube.com/watch?v=LQ6pFgQXQ0Q



[EOF]
