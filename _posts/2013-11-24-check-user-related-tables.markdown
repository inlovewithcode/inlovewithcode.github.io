---
author: guidedmissile
comments: true
date: 2013-11-24 13:11:06+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/check-user-related-tables/
slug: check-user-related-tables
title: CHECK USER RELATED TABLES
wordpress_id: 28
categories:
- Oracle
tags:
- SQL
---

HOW TO CHECK USER RELATED TABLES

    
    
    SELECT * FROM CAT;
    
    SELECT * FROM USER_TABLES  WHERE TABLE_NAME LIKE '%my_app_table%';
    SELECT * FROM USER_VIEWS WHERE VIEW_NAME LIKE '%my_app_view%';
    
    SELECT * FROM SYS.DBA_TABLES WHERE OWNER='username';
    SELECT * FROM SYS.DBA_OBJECTS WHERE OWNER ='owner_name';
    
