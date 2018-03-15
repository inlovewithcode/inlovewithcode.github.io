---
author: guidedmissile
comments: true
date: 2013-11-24 07:06:42+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/check-partisioned-tables-sizes/
slug: check-partisioned-tables-sizes
title: Check Partisioned Tables sizes
wordpress_id: 9
categories:
- Oracle
tags:
- SQL
---

Checks for all the table partisions(space) details present under a specific TABLE_NAME

    
    select
        owner,
        segment_name,
        partition_name,
        segment_type,
        bytes / 1024/1024 "MB" 
    from
        dba_segments --System Table
    where 
        lower(SEGMENT_NAME) like 'TABLE_NAME%'
