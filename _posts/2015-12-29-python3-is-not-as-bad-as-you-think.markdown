---
author: guidedmissile
comments: false
date: 2015-12-29 10:35:51+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/12/29/python3-is-not-as-bad-as-you-think/
slug: python3-is-not-as-bad-as-you-think
title: Python3 is not as bad as you think !
wordpress_id: 720
categories:
- Python
post_format:
- Aside
---

I personally did not like to believe my beloved Python 2.7 has come to an end. Like anyone I was a bit stubborn to things and I see I have already gotten a bit religious about Py2.7 - as my mentor says(scolds me) I agree its a bit(not actually) bad but I am proud of it.

So here I am, started off exploring with Python where I like that concept of (1) new **concurrent** module where you can do multithreading with a new **map** function, well is nt that simply great !? :)

(2) Secondly favourite things I like is explicit and implicit exception handling where some intelligent cleanup is done so next when a type-error happens you don't get 10 - 15 lines of code I think, just 2-3 line of err is enough.

(3) **IO, Decimal** Modules is re-written to increase to increase performance. **Import** module is re-written to handle deadlock issues created while every thread tried to import same module( good luck to those VM guys who are running different kinds of Hardware platforms). Sta

(4)new module - "ipaddress", thank god - I don't have to define and check about them every time :) - Lazyness rocks !! ;)

(5) virtualenv pkg is default pkg now.

(6) Inside of classes now we can use  => __name__ + ‘.’ + self.__qualname__ # and it gives you fully qualified name. There is also another parameter called METACLASS inside of each by default

    
    (7) Extended iterable unpacking - below is valid now
    first, *rest = range(5) 
    first, *mid, last = range(12)


(8) If recall properly, by now you should know that everything in python is objects mostly and it maintain __dict__ for each. So what happened here in Py3.3, these memory views are rewritten to maintain to one mega view I think and it made python work faster. Thumbs up !!

Here is a set of things I have kept as a notes for myself. If you are further interested, you can find 40+ min presentation over Youtube.

My **Notes :**



	
  * Traceback - Module # clean-up for error codes


![Screen Shot 2015-12-28 at 7.23.21 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-28-at-7-23-21-pm.png)![Screen Shot 2015-12-28 at 7.24.31 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-28-at-7-24-31-pm.png)



	
  * Explicit exception chaining


![Screen Shot 2015-12-28 at 7.25.43 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-28-at-7-25-43-pm.png)



	
  * Module : importlib


![Screen Shot 2015-12-28 at 7.26.43 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-28-at-7-26-43-pm.png)

![Screen Shot 2015-12-28 at 7.27.28 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-28-at-7-27-28-pm.png)

![Screen Shot 2015-12-28 at 7.28.33 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-28-at-7-28-33-pm.png)

For above image - If you have few codes which are already compiled to .pyc, then they don't get re-written but new ones will be created inside __pycache__ directory.





	
  * Namespace packages


![Screen Shot 2015-12-28 at 7.30.10 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-28-at-7-30-10-pm.png)



	
  * Python3 with standard API functions as defaults


![Screen Shot 2015-12-28 at 7.32.43 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-28-at-7-32-43-pm.png)



	
  * Function annotations # Security & ease testing


![Screen Shot 2015-12-28 at 7.33.40 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-28-at-7-33-40-pm.png)![Screen Shot 2015-12-28 at 7.34.31 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-28-at-7-34-31-pm.png)



	
  * Thanks ASCII and hello to UTF-8 !


![Screen Shot 2015-12-28 at 7.36.03 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-28-at-7-36-03-pm.png)



	
  * String literals : new UTF-8 stuff !


![Screen Shot 2015-12-28 at 7.36.39 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-28-at-7-36-39-pm.png)![Screen Shot 2015-12-28 at 7.38.47 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-28-at-7-38-47-pm.png)![Screen Shot 2015-12-28 at 7.40.18 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-28-at-7-40-18-pm.png)



Conclusion : Performance or 2.7 & 3.3 are same :)

Below is comparison specific to packages.

![Screen Shot 2015-12-28 at 7.43.37 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-28-at-7-43-37-pm.png)


