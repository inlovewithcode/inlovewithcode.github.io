---
author: guidedmissile
comments: false
date: 2016-12-25 10:21:37+00:00
layout: page
link: https://inlovewithcode.wordpress.com/ipython/
slug: ipython
title: Jupyter - ipython
wordpress_id: 1633
---

## Utility tips



[code lang=text]
# reload modules for every 2 seconds
#    use for experiment with new modules
%load_ext autoreload
%autoreload 2

# to make results reproduceble
import numpy as np
seed = 7 * 9
np.random.seed(seed)

# plotting
import matplotlib.pyplot as plt
%matplotlib inline


# disable simple warnings
import warnings
warnings.filterwarnings('ignore')
[/code]



## Ipython/ Jupyter - Interactive Functions Introduction



Imports

[code lang="Python"]
from __future__ import print_function
from ipywidgets import interact, interactive, fixed
import ipywidgets as widgets
[/code]

Usecase1

[code lang="Python"]
# function
f = lambda x: return x

# user input slider
interact(f, x=10);
[/code]

Usecase2: How to set default values and a range?

[code lang="Python"]
def f(x=80): return x

interact(f, x=(0, 100, 0.5);
[/code]



## Ipython-Jupyter UI Enhancements



Try complete themes from [https://github.com/dunovank/jupyter-themes](https://github.com/dunovank/jupyter-themes)

Try custom and more versatile options from [https://github.com/transcranial/jupyter-themer](https://github.com/transcranial/jupyter-themer)

For Jupter-themer, let us have a UI extension to make it easy for us. [https://github.com/merqurio/jupyter_themes](https://github.com/merqurio/jupyter_themes)

[code lang="text"]
# check if folder is already there
ls -l $(jupyter --data-dir)/nbextensions

# If required* create folder (optional)
mkdir -p $(jupyter --data-dir)/nbextensions

# creating a sub-folder for Jupyter extensions to reside (optional)
cd $(jupyter --data-dir)/nbextensions

# create a folder for themes
$ mkdir jupyter_themes && cd jupyter_themes

# downloading themes code
$ wget https://raw.githubusercontent.com/merqurio/jupyter_themes/master/theme_selector.js

# Activate the extension
$ cd ../ && jupyter nbextension enable jupyter_themes/theme_selector
[/code]

Source:
* http://ipywidgets.readthedocs.io/en/latest/examples/Using%20Interact.html
