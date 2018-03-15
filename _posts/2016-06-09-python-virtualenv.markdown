---
author: guidedmissile
comments: true
date: 2016-06-09 20:20:12+00:00
excerpt: 'This Python post is about installing, activate &amp; deactivate a virtual
  environment in python. A virtual environment is like a virtual machine for python/like
  a jail in BSD/ like a docker. This is to create a python environment that is ideal
  for development/testing/manage inter-package dependencies. '
layout: post
link: https://inlovewithcode.wordpress.com/2016/06/10/python-virtualenv/
slug: python-virtualenv
title: Python VirtualEnv Tips
wordpress_id: 1110
categories:
- Python
tags:
- virtualenv
---

This post is about installing, activate & deactivate a virtual environment in python. A virtual environment is like a virtual machine for python/like a jail in BSD/ like a docker. This is to create a python environment that is ideal for development/testing/manage inter-package dependencies.



## Create a python virtual environment




    
    <code><span class="pln"><span class="pun"><span class="pln">########## Installation
    
    # to install virtualenv
    pip install virtualenv
    
    # post installation virtualenv will be available as commandline tool
    # you run `which virtualenv` to check if its installed
    # you can also run `pip show virtualenv` for more details
    
    ########## Utilisation of virtualenv
    
    # create a virtual envirnoment
    $ virtualenv </span><span class="pun">env
    </span><span class="pln">
    # create a virtual environment folder named 'env'
    $ virtualenv </span><span class="pun">env</span>
    <span class="pln">
    # create a virtual environment folder named 'env'(with python2.7)
    $ virtualenv -p python2.7 </span><span class="pun">env
    </span></span><span class="pln">
    # create a virtual environment folder named 'env' with python3.5
    $ virtualenv -p python3.5 </span><span class="pun">env</span>
    </span></code>





## Quick way install all system packages in virtual environment




    
    <code><span class="pln"><span class="pun"><span class="pln"># To install(copy*) all OS packages into your env
    $ virtualenv --sytem-site-packages env
    
    
    # using PIP to install packages from a requirements.txt
    </span><span class="pun"># pip install -r requirement.txt</span></span></span></code>





## Activate & Deactivate Virtual Env




    
    <code><span class="pln"><span class="pun"><span class="pln"># To install all OS packages into your virtual environment
    $ virtualenv --sytem-site-packages env
    
    </span># Now you will see a env folder
    $ ls
    env
    
    # activate virtual env -- note how your prompt changes
    $ source env/bin/activate
    (env)$ 
    
    # to deactivate
    (env)$ deactivate
    $</span></span></code>





## Clone a python virtual environment




    
    <code><span class="pln"><span class="pun"><span class="pln">############ Installation
    # pip install virtualenv-clone
    
    # copy a virtual envirnoment 'env' to 'env2'
    $ virtualenv-clone </span><span class="pun">env env2
    </span></span></span></code>



To Make virtual environment inherit **specific** packages from your global site-packages?

Create the environment with `virtualenv --system-site-packages` . Then, activate the virtual environment and when you install packages, use `pip install --ignore-installed` or `pip install -I` . That way pip will install what you've requested **locally** even though a system-wide version exists. Your python interpreter will look first in the virtual environment's package directory, so those packages should shadow the global ones.



### Anaconda/Conda/Miniconda



Conda is a tool for managing and deploying applications, environments, and packages. If you are using Conda/Mini-Conda/Anaconda, then you would have use following way to create virtual environments. This is because, Conda as a package manager want to have version control, and keep records of all virtual environments.

**Check conda install & version**

`


    
    
    SDS-bash3.2$ conda -V
    conda 4.3.17
    



`

**Check Existing Environments**

`


    
    
    SDS-bash3.2$ conda info --env
    # conda environments:
    #
    python2                  /Users/sampathm/miniconda3/envs/python2
    tensorflow               /Users/sampathm/miniconda3/envs/tensorflow
    root                  *  /Users/sampathm/miniconda3
    



`

**Create a virtual environment**

`


    
    
    $ conda create -n python27 python=2.7
    



`

**Start a virtual environment**
`


    
    
    $ source activate python27
    



`

**Create a virtual environment**

`


    
    
    $ deactivate
    



`

**Remove a virtual environment**

`


    
    
    $ conda info --env
    # conda environments:
    #
    python27                  /Users/sampathm/miniconda3/envs/python27
    python2                  /Users/sampathm/miniconda3/envs/python2
    tensorflow               /Users/sampathm/miniconda3/envs/tensorflow
    root                  *  /Users/sampathm/miniconda3
    
    SDS-bash3.2$ conda remove -n python27 --all
    



`

Source:
* https://conda.io/docs/using/envs.html
* http://stackoverflow.com/questions/14571454/virtualenv-specifing-which-packages-to-use-system-wide-vs-local
