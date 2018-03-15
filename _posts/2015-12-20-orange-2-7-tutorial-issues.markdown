---
author: guidedmissile
comments: false
date: 2015-12-20 11:59:57+00:00
excerpt: Oracle 2.7, Data visualisation tool if throws you error while reading tutorials
  then check this post !
layout: post
link: https://inlovewithcode.wordpress.com/2015/12/20/orange-2-7-tutorial-issues/
slug: orange-2-7-tutorial-issues
title: 'Orange 2.7 # Tutorial Issues !!'
wordpress_id: 701
categories:
- Python
tags:
- Orange
---

Incase if you are experiencing following error while using Anaconda / Orange 2.7 while checking tutorials,..

Error:` KeyError Traceback (most recent call last): File "C:\Python27\lib\site-packages\Orange\OrangeWidgets\OWWidget.py", line 178, in reportAndFinish self.sendReport() File "C:\Python27\lib\site-packages\Orange\OrangeWidgets\Data\OWDataTable.py", line 520, in sendReport table = self.id2table[id] KeyError: None `

**Solution** : Kindly first select "File" first. This error because there is no file exists to generate a report.  First time when you open tutorials, Orange asks you to download packages. These contain sample datasets to try. If you have downloaded them, you would see as below.

![Screen Shot 2015-12-20 at 5.31.08 pm](https://inlovewithcode.files.wordpress.com/2015/12/screen-shot-2015-12-20-at-5-31-08-pm.png)





Simply select it then, a pop window open showing a list of sample data sets. Good Luck. Cheers !
