---
author: guidedmissile
comments: true
date: 2013-11-24 13:07:36+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/list-all-stored-procedures/
slug: list-all-stored-procedures
title: LIST ALL STORED PROCEDURES
wordpress_id: 26
categories:
- Oracle
tags:
- SQL
---

SELECT * FROM USER_PROCEDURES;
    
    SELECT * FROM DBA_PROCEDURES;
    
    SELECT * FROM USER_SOURCE WHERE NAME = 'STORED_PROC';
    
    SELECT * FROM DBA_SOURCE WHERE NAME = 'STORED_PROC';
