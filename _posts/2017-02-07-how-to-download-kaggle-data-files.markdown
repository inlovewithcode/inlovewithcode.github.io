---
author: guidedmissile
comments: true
date: 2017-02-07 18:57:10+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2017/02/08/how-to-download-kaggle-data-files/
slug: how-to-download-kaggle-data-files
title: How to download Kaggle Data Files?
wordpress_id: 1654
categories:
- Python
---

## Method 1: Using Chrome App & wget






    
  * Step1: Get Chrome Widget: https://chrome.google.com/webstore/detail/cookietxt-export/lopabhfecdfhgogdbojmaicoicjekelh/related

    
  * Step2: Login to you Kaggle HomePage and then check you cookies details(testing above app is if working).

    
  * Step3: Go to command line where you want to download details and here create a file named `cookies`

    
  * step4: run following type of command



[code lang=bash]
wget --load-cookies=cookies
[/code]

For large files like I have here `stage1.7z` from Data Science Bowl 2017 @ Kaggle, I use the following snippet to check how well download is going on,.

[code lang=bash]
for i in {1..100}; do sleep 20; ls -l stage1.7z; done
[/code]



## Meathod2: Using Python Script






    
  * Step1: Get a copy of following file - https://raw.githubusercontent.com/grahamannett/kaggleDownloader/master/main.py

    
  * Step2: Run above script to check for help. (I'm planning to work in this project to make it more easy to download tools).


