---
author: guidedmissile
comments: false
date: 2017-04-05 16:06:08+00:00
layout: page
link: https://inlovewithcode.wordpress.com/about/anaconda_venv/
slug: anaconda_venv
title: ANACONDA Virtual Env's
wordpress_id: 2001
---

Conda Version I use: `conda 4.3.13`
Default Python Version: `Python 3.5.2 :: Continuum Analytics, Inc.`



# How to create a separate environment using Anaconda?



Imagine you have to create an environment called py33 by using:

_Creating Env_

Example:
    conda create -n py33 python=3.3 anaconda

Creating Python2.7
    conda create -p experiment_env python=2.7 pip

_Activate Env_


    
    <code>source activate py33
    </code>



_Deactivate Enc_


    
    <code>source deactivate
    </code>



Source: http://stackoverflow.com/questions/20081338/how-to-activate-an-anaconda-environment#21707160
