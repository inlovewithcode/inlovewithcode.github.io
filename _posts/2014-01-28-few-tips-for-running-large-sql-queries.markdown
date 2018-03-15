---
author: guidedmissile
comments: true
date: 2014-01-28 10:10:55+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2014/01/28/few-tips-for-running-large-sql-queries/
slug: few-tips-for-running-large-sql-queries
title: Few tips for running large sql queries
wordpress_id: 111
categories:
- Oracle
---

Every time we try to run some sql queries, Oracle tries to read interpret queries to understand if user inputs is required. If the sql query is having (&) any where, then it will ask user for input. User below if do not want oracle to just run without reading.

    
    set scan off;


If you are running large queries, its advised to put commit statement in the middle. I prefer to put it for every 500 insert query statements.

    
    commit;
