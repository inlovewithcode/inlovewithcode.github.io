---
author: guidedmissile
comments: true
date: 2016-06-18 12:26:54+00:00
excerpt: explains how to customise or modify or make your IPython terminal prompt
  or shell look like standard python prompt
layout: post
link: https://inlovewithcode.wordpress.com/2016/06/18/ipython-prompt-customisation/
slug: ipython-prompt-customisation
title: iPython Prompt Customisation
wordpress_id: 1140
categories:
- Python
post_format:
- Aside
tags:
- IPython
- prompt customisation
---

It might look silly but I really don't like IPython prompt so much !! As for capabilities of IPython, it's just really amazing. So how?

Here you can learn, how you can convert IPython prompt look like Python standard prompt.

from IPython terminal run following commands without # in the start.


<blockquote>>>> #%config PromptManager.out_template = ""
>>> #%config PromptManager.in_template = "ip >>> "
>>> #%config TerminalInteractiveShell.separate_in = ''</blockquote>



    
    # To copy paste - use below
    %config PromptManager.in_template = "ip >>> "
    %config PromptManager.out_template = ""
    %config TerminalInteractiveShell.separate_in = ''


You can also add these into you IPython profile just like we do for bash and other. Once you setup there I think you know what happens.

In case you want special color for your prompt, kindly check the second link in sources mention at the bottom of this post.

Advantages



	
  * makes you feel comfortables about IPython which is what Python is all about.

	
  * no unnecessary waste of space.

	
  * removes tracker like showing numbers for input command and output command.


Sources:

	
  * [https://ipython.org/ipython-doc/2/interactive/shell.html#prompt-customization](https://ipython.org/ipython-doc/2/interactive/shell.html#prompt-customization)

	
  * [https://github.com/ipython/ipython/wiki/Cookbook:-Dynamic-prompt](https://github.com/ipython/ipython/wiki/Cookbook:-Dynamic-prompt)

	
  * [http://stackoverflow.com/questions/2351857/ipython-single-line-spacing-possible](http://stackoverflow.com/questions/2351857/ipython-single-line-spacing-possible)




Examples:

Here is me, trying lots of combos

    
    ip >>> %config PromptManager.in_template = "{color.Normal}ip >>> "
    ip >>> %config PromptManager.in_template = "{color.Red}ip >>> "
    ip >>> %config PromptManager.in_template = "{color.Black}ip >>> "
    ip >>> %config PromptManager.in_template = "{color.Green}ip >>> "
    ip >>> %config PromptManager.in_template = "{color.Yellow}ip >>> "
    ip >>> %config PromptManager.in_template = "{color.BlinkYellow}ip >>> "
    ip >>> %config PromptManager.in_template = "{color.BlinkLightGray}ip >>> "
    ip >>> print 1
    1
    ip >>>


use color.Normal, to get standard dark green.



Troubleshooting:

In case you type error in color name, then error like below will come. To provide an example, I tried color.**BlinkLightGray1**, which is not in the predefined list for IPython prompt and below is the error I received.

    
    AttributeError: InputTermColors instance has no attribute 'BlinkLightGray1'


Solution: After this error is thrown, you will still in IPython prompt. So now, click up arrow to get your previous command and then correct it and enter.



Adios:

wow, it's pretty amazing when I try these things in terminal. Good Luck :)
