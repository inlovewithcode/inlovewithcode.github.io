---
author: guidedmissile
comments: true
date: 2013-11-24 07:19:18+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/sql-case-statement/
slug: sql-case-statement
title: SQL Case Statement
wordpress_id: 13
categories:
- Oracle
tags:
- SQL
---

Example of how to use case statement

    
    SELECT cust_last_name,
       CASE credit_limit
        WHEN 100 THEN 'LOW'
        WHEN 5000 THEN 'HIGH'
        ELSE 'MEDIUM' 
       END
       FROM customers


Using this 'CASE', we are printing salary information as 'HIGH'/'LOW'/'MEDIUM' instead of salary credit_limit.
