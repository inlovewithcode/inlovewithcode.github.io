---
author: guidedmissile
comments: false
date: 2016-11-13 08:09:52+00:00
excerpt: What you need to learn in GIT for doing OpenSource Development.
layout: page
link: https://inlovewithcode.wordpress.com/about/opensource-development/
slug: opensource-development
title: OpenSource Development
wordpress_id: 1536
---

# Git OpenSource Development





## Introduction



Learn basic command like follow
* git init
* git clone
* git branch
* git checkout
* git diff
* git merge
* git add
* git apply & git apply -R

By now you would have learned how to do all basic operations of using git. For OpenSource development, you would need to know these details.



## How to setup a git repo?








### **Quick setup** — if you’ve done this kind of thing before







We recommend every repository include a README, LICENSE, and .gitignore.














### …or create a new repository on the command line






    
    <span class="user-select-contain">echo "# test" >> README.md</span>
    <span class="user-select-contain">git init</span>
    <span class="user-select-contain">git add README.md</span>
    <span class="user-select-contain">git commit -m "first commit"</span>
    <span class="user-select-contain">git remote add origin <strong><span class="js-git-clone-help-text">https://github.com/..yourname../..git</span></strong></span>
    <span class="user-select-contain">git push -u origin master</span>
    














### 




### …or push an existing repository from the command line






    
    <span class="user-select-contain">git remote add origin <strong><span class="js-git-clone-help-text">https://github.com/..yourname.../..git</span></strong></span>
    <span class="user-select-contain">git push -u origin master</span>













## How to copy a git repo to your local system?










    
    <span class="user-select-contain">git clone <<strong><span class="js-git-clone-help-text">https://github.com/...yourname..../..git></span></strong></span>













## How to fork a git repo and send a pull request?





### Fork a git repo



Fork/ Forking a git repo means taking a copy of repository for yourself. This helps you to do either research on that code for yourself to develop that tool for community & help them fix bugs, add features and enjoy open source development.

Step1: Got to repo you wish to contribution or learn about

Step2: Check for Fork button and click it.



## Get your local copy



Step1: Go the folder location where you want to save your code

Step2: Run below command.


    
    <code>clone <span class="hljs-tag"><<span class="hljs-title">your</span> <span class="hljs-attribute">git</span> <span class="hljs-attribute">repo</span> <span class="hljs-attribute">link</span>></span> <span class="hljs-tag"><<span class="hljs-title">foldername</span>></span></code>



Folder name is optional here. From this local repo, you can do all your development.



## Pull request



Pull request is a way to send developed code changes to community repo.

Step1: Commit your changes.

Step2: Push code the changes to github repository

Step2: Go to your GitHub repo as shown here ([https://youtu.be/G1I3HF4YWEw?t=301)(prefer](https://youtu.be/G1I3HF4YWEw?t=301)(prefer) checking this video) and click check & pull request.



<blockquote>Source: [https://www.youtube.com/watch?v=G1I3HF4YWEw](https://www.youtube.com/watch?v=G1I3HF4YWEw)</blockquote>



Source: [https://www.youtube.com/watch?v=e3bjQX9jIBk](https://www.youtube.com/watch?v=e3bjQX9jIBk) [10 mins Introduction]



## How to update your forked repo from parent repository?





#### Background information



I have forked _yip_ module repo from balzss to help him with little development if possible and also learn a bit about open source development. So I have a repo at [https://github.com/msampathkumar/yip.git](https://github.com/msampathkumar/yip.git), which you can check. Last night it seems our friend(balzss) did little code clean and over repo is not yet up to date.

Here are the steps of how to update your repo from parent developer repo.
Note:
* parent developer’s(balzss) git repo is at [https://github.com/balzss/yip.git](https://github.com/balzss/yip.git)
* my git repo is at [https://github.com/msampathkumar/yip.git](https://github.com/msampathkumar/yip.git)

my prompt looks like below


    
    <code class=" hljs css">(<span class="hljs-tag">env</span>)➜  <span class="hljs-tag">yip</span> <span class="hljs-tag">git</span><span class="hljs-pseudo">:(development)</span> ✗
    (<span class="hljs-tag">env</span>)➜  <span class="hljs-tag">yip</span> <span class="hljs-tag">git</span><span class="hljs-pseudo">:(development)</span> ✗ <span class="hljs-tag">date</span>
    <span class="hljs-tag">Sun</span> <span class="hljs-tag">Nov</span> 13 11<span class="hljs-pseudo">:41</span><span class="hljs-pseudo">:45</span> <span class="hljs-tag">IST</span> 2016</code>



Step1: Check you current repo status


    
    <code class=" hljs avrasm">(env)➜  yip git:(development) ✗ git remote -v
    origin  https://github<span class="hljs-preprocessor">.com</span>/msampathkumar/yip<span class="hljs-preprocessor">.git</span> (fetch)
    origin  https://github<span class="hljs-preprocessor">.com</span>/msampathkumar/yip<span class="hljs-preprocessor">.git</span> (<span class="hljs-keyword">push</span>)</code>



Step2: Add an upstream link to pull update from parent development code


    
    <code>(env)➜  yip git:(development) ✗ git remote <span class="hljs-keyword">add</span> upstream https://github<span class="hljs-preprocessor">.com</span>/balzss/yip<span class="hljs-preprocessor">.git</span></code>



Step3: Check the if you can see upstream branches


    
    <code class=" hljs avrasm">(env)➜  yip git:(development) ✗ git remote -v
    origin  https://github<span class="hljs-preprocessor">.com</span>/msampathkumar/yip<span class="hljs-preprocessor">.git</span> (fetch)
    origin  https://github<span class="hljs-preprocessor">.com</span>/msampathkumar/yip<span class="hljs-preprocessor">.git</span> (<span class="hljs-keyword">push</span>)
    upstream    https://github<span class="hljs-preprocessor">.com</span>/balzss/yip<span class="hljs-preprocessor">.git</span> (fetch)
    upstream    https://github<span class="hljs-preprocessor">.com</span>/balzss/yip<span class="hljs-preprocessor">.git</span> (<span class="hljs-keyword">push</span>)</code>



Step4: Pull update from parent repo and merge these changes into you master and development branches

Note: I have two branch _master_ and _development_, So I have to update both of them


    
    <code class=" hljs fsharp">(env)➜  yip git:(development) ✗ git fetch upstream
    remote: Counting objects: <span class="hljs-number">4</span>, <span class="hljs-keyword">done</span>.
    remote: Compressing objects: <span class="hljs-number">100</span>% (<span class="hljs-number">4</span>/<span class="hljs-number">4</span>), <span class="hljs-keyword">done</span>.
    remote: Total <span class="hljs-number">4</span> (delta <span class="hljs-number">0</span>), reused <span class="hljs-number">0</span> (delta <span class="hljs-number">0</span>), pack-reused <span class="hljs-number">0</span>
    Unpacking objects: <span class="hljs-number">100</span>% (<span class="hljs-number">4</span>/<span class="hljs-number">4</span>), <span class="hljs-keyword">done</span>.
    From https:<span class="hljs-comment">//github.com/balzss/yip</span>
     * [<span class="hljs-keyword">new</span> branch]      develop    -> upstream/develop
     * [<span class="hljs-keyword">new</span> branch]      master     -> upstream/master
    </code>



Step5: Update your branches with upstream master


    
    <code class=" hljs livecodeserver">(env)➜  yip git:(development) ✗ git branch
    * development
      master
    (env)➜  yip git:(development) ✗ git checkout master
    Switched <span class="hljs-built_in">to</span> branch <span class="hljs-string">'master'</span>
    Your branch is up-<span class="hljs-built_in">to</span>-<span class="hljs-built_in">date</span> <span class="hljs-operator">with</span> <span class="hljs-string">'origin/master'</span>.
    (env)➜  yip git:(master) ✗ git checkout master
    Already <span class="hljs-command"><span class="hljs-keyword">on</span> <span class="hljs-string">'master'</span></span>
    Your branch is up-<span class="hljs-built_in">to</span>-<span class="hljs-built_in">date</span> <span class="hljs-operator">with</span> <span class="hljs-string">'origin/master'</span>.
    (env)➜  yip git:(master) ✗ git <span class="hljs-built_in">merge</span> upsteam/master
    <span class="hljs-built_in">merge</span>: upsteam/master - <span class="hljs-operator">not</span> something we can <span class="hljs-built_in">merge</span>
    (env)➜  yip git:(master) ✗ git remote -v
    origin  <span class="hljs-keyword">https</span>://github.com/msampathkumar/yip.git (fetch)
    origin  <span class="hljs-keyword">https</span>://github.com/msampathkumar/yip.git (push)
    upstream    <span class="hljs-keyword">https</span>://github.com/balzss/yip.git (fetch)
    upstream    <span class="hljs-keyword">https</span>://github.com/balzss/yip.git (push)
    (env)➜  yip git:(master) ✗ git branch
      development
    * master
    (env)➜  yip git:(master) ✗ git <span class="hljs-built_in">merge</span> upstream/master
    Updating f071330..d5c8c59
    Fast-forward
     yip | <span class="hljs-number">145</span> +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++<span class="hljs-comment">----------------------------------------------------------------</span>
     <span class="hljs-number">1</span> <span class="hljs-built_in">file</span> changed, <span class="hljs-number">81</span> insertions(+), <span class="hljs-number">64</span> deletions(-)
    (env)➜  yip git:(master) ✗</code>



Step6: Push you local code changes to you home git repo


    
    <code class=" hljs lasso">(env)➜  yip git:(master) ✗ git push
    Counting objects: <span class="hljs-number">10</span>, done<span class="hljs-built_in">.</span>
    Delta compression using up <span class="hljs-keyword">to</span> <span class="hljs-number">4</span> threads<span class="hljs-built_in">.</span>
    Compressing objects: <span class="hljs-number">100</span><span class="hljs-subst">%</span> (<span class="hljs-number">4</span>/<span class="hljs-number">4</span>), done<span class="hljs-built_in">.</span>
    Writing objects: <span class="hljs-number">100</span><span class="hljs-subst">%</span> (<span class="hljs-number">4</span>/<span class="hljs-number">4</span>), <span class="hljs-number">822</span> <span class="hljs-built_in">bytes</span> <span class="hljs-subst">|</span> <span class="hljs-number">0</span> <span class="hljs-built_in">bytes</span>/s, done<span class="hljs-built_in">.</span>
    Total <span class="hljs-number">4</span> (delta <span class="hljs-number">2</span>), reused <span class="hljs-number">0</span> (delta <span class="hljs-number">0</span>)
    remote: Resolving deltas: <span class="hljs-number">100</span><span class="hljs-subst">%</span> (<span class="hljs-number">2</span>/<span class="hljs-number">2</span>), completed <span class="hljs-keyword">with</span> <span class="hljs-number">2</span> <span class="hljs-built_in">local</span> objects<span class="hljs-built_in">.</span>
    <span class="hljs-keyword">To</span> https:<span class="hljs-comment">//github.com/msampathkumar/yip.git</span>
       f071330<span class="hljs-built_in">..</span>d5c8c59  master <span class="hljs-subst">-> </span>master
    (env)➜  yip git:(master) ✗ git branch <span class="hljs-attribute">-a</span>
      development
    <span class="hljs-subst">*</span> master
      remotes/origin/HEAD <span class="hljs-subst">-> </span>origin/master
      remotes/origin/develop
      remotes/origin/development
      remotes/origin/master
      remotes/upstream/develop
      remotes/upstream/master
    (env)➜  yip git:(master) ✗ git pull
    Already up<span class="hljs-attribute">-to</span><span class="hljs-attribute">-date</span><span class="hljs-built_in">.</span></code>



Step7: Now update your local development branch also.


    
    <code class=" hljs livecodeserver">(env)➜  yip git:(master) ✗ git checkout master
    Already <span class="hljs-command"><span class="hljs-keyword">on</span> <span class="hljs-string">'master'</span></span>
    Your branch is up-<span class="hljs-built_in">to</span>-<span class="hljs-built_in">date</span> <span class="hljs-operator">with</span> <span class="hljs-string">'origin/master'</span>.
    (env)➜  yip git:(master) ✗ git checkout development
    Switched <span class="hljs-built_in">to</span> branch <span class="hljs-string">'development'</span>
    Your branch is up-<span class="hljs-built_in">to</span>-<span class="hljs-built_in">date</span> <span class="hljs-operator">with</span> <span class="hljs-string">'origin/development'</span>.
    (env)➜  yip git:(development) ✗ git <span class="hljs-built_in">merge</span> master
    Updating d7f2f40..d5c8c59
    Fast-forward
     yip | <span class="hljs-number">48</span> ++++++++++++++++++++++++<span class="hljs-comment">------------------------</span>
     <span class="hljs-number">1</span> <span class="hljs-built_in">file</span> changed, <span class="hljs-number">24</span> insertions(+), <span class="hljs-number">24</span> deletions(-)
    (env)➜  yip git:(development) ✗ git pull
    Already up-<span class="hljs-built_in">to</span>-<span class="hljs-built_in">date</span>.</code>



Summary:
* Add parent repo to your remote repo
* Merge remote branch master code into your local branch master code
* Update your local branch master code to git repo
* Also update your development branch from your master

Source: [https://www.youtube.com/watch?v=-zvHQXnBO6c](https://www.youtube.com/watch?v=-zvHQXnBO6c)
