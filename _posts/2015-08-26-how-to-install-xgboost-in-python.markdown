---
author: guidedmissile
comments: false
date: 2015-08-26 10:22:41+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/08/26/how-to-install-xgboost-in-python/
slug: how-to-install-xgboost-in-python
title: How to install xgboost in python?
wordpress_id: 598
categories:
- Python
tags:
- Xgboost
---

![dmlc XGBOOST](https://raw.githubusercontent.com/dmlc/dmlc.github.io/master/img/logo-m/xgboost.png)

XGBOOST

_If you are using ANACONDA, please check below link for instructions_




    
  * _[https://anaconda.org/akode/xgboost](https://anaconda.org/akode/xgboost)_




    
    <em><span style="color:#999999;"><strong>Shell Command</strong>:</span></em>
    
    <em><span style="color:#999999;">conda install -c <a style="color:#999999;" href="https://conda.anaconda.org/akode">https://conda.anaconda.org/akode</a> xgboost</span></em>



If you want to do it on your own, here comes a short guide to compile and install xgboost from source on win64:

1) Download & install Git for win64: [https://git-scm.com/download/win](https://git-scm.com/download/win)

2) Download & install mingw-w64: [http://sourceforge.net/projects/mingw-w64/](http://sourceforge.net/projects/mingw-w64/)

3) Let's assume we have the following installation paths: C:\mingw64 and C:\Program Files\git => Add the following paths to your windows environment PATH: C:\mingw64\bin and c:\programs\Git\cmd

4) Start cmd.exe and check if you can run git and gcc from command line




    
  * type gcc, you should get: "gcc: fatal error: no input files"

    
  * type make, you should get: "make: _*_ No targets specified and no makefile found. Stop."

    
  * type git, you should get ... u get it



5) Let's create C:\mypy. Open an command prompt an cd to this folder. Type git clone[https://github.com/dmlc/xgboost.git](https://github.com/dmlc/xgboost.git)

6) cd to c:\mypy\xgboost and type make. Xgboost should compile now. Afterwards type list | grep xgb and it should list "xgboost.exe"

7) cd to c:\mypy\xgboost\python-package and type python setup.py install

8) do not build better xgboost models then I do :P

Complete thread -[https://www.kaggle.com/c/liberty-mutual-group-property-inspection-prediction/forums/t/16120/how-to-xgboost-in-python-3-4-3-anaconda-2-2-0-64-bit/90416#post90416](https://www.kaggle.com/c/liberty-mutual-group-property-inspection-prediction/forums/t/16120/how-to-xgboost-in-python-3-4-3-anaconda-2-2-0-64-bit/90416#post90416)

Thank you [Faron](https://www.kaggle.com/mmueller), for your quick/supportive help.



**_Note: Since the time this post has been written, there were many updates to _**Xgbo0st******_ and Anaconda. I would request to kindly use Anaconda - Python Setup with Packages or Miniconda(a simpler version of Anaconda) for installing _Xgbo0st_._**
