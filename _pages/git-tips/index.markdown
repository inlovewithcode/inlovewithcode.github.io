---
author: guidedmissile
comments: false
date: 2016-12-02 10:09:44+00:00
layout: page
link: https://inlovewithcode.wordpress.com/git-tips/
slug: git-tips
title: GIT TIPS
wordpress_id: 1579
---

### How to apply or rollback a git patch or git diff code changes?


say you patch file is **myfix.diff**.

To apply code changes




    
    <code class="language-none">git apply   myfix.diff</code>





To rollback a complete git patch




    
    <code class="language-none">git apply   -R myfix.diff</code>





To rollback change to a particular file




    
    <code class="language-none">git checkout <filename></code>







### How to do git merge?


say you are in **branch1** and **branch2** has the new code changes.




    
    <code class="language-none">git merge branch2</code>





This takes the code changes in **branch2** and puts them in **branch1**.


### How to take last commit code details?


Commit details include username, user commit note, time and hashid.

Code details, as name details include code differences.

For last `commit` code changes use




    
    <code class="language-none">git show</code>





For last but one or say from last second commit




    
    <code class="language-none">git show HEAD~1</code>





For last but second or say from last third commit




    
    <code class="language-none">git show HEAD~2</code>







### How to show in a concise way of looking at git commits?






    
    <code class="language-none">git log --pretty=oneline</code>



