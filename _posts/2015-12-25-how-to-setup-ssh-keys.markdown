---
author: guidedmissile
comments: false
date: 2015-12-25 18:39:02+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/12/26/how-to-setup-ssh-keys/
slug: how-to-setup-ssh-keys
title: How to Setup SSH Keys?
wordpress_id: 716
categories:
- Linux Scripting
tags:
- Shell Scripting
---

Here are detailed steps of how to copy ssh keys



	
  * Step 1:
% **cd ~/.ssh**
% **ssh-keygen -t rsa1**
Generating public/private rsa1 key pair.
Enter file in which to save the key (~/.ssh/identity): (just type return) 
Enter passphrase (empty for no passphrase): (just type return) Enter same passphrase again: (just type return) 
Your identification has been saved in ~/.ssh/identity
Your public key has been saved in ~/.ssh/identity.pub
The key fingerprint is:
Some really long string
%

	
  * Step 2:
Then, paste content of the local ~/.ssh/identity.pub file into the file ~/.ssh/authorized_keys on the remote host.




Source: [http://www.ece.uci.edu/~chou/ssh-key.html](http://Source)
