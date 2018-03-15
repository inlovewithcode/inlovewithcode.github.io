---
author: guidedmissile
comments: true
date: 2013-11-24 13:00:46+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/print-records-with-serial-numbers/
slug: print-records-with-serial-numbers
title: Print records with Serial Numbers
wordpress_id: 22
categories:
- Oracle
tags:
- SQL
---

EXAMPLES FOR PRINTING "ROW NUMBERS" WITH "ORDER BY OPTION"

    
    SELECT ROW_NUMBER() OVER (ORDER BY A.FULL_NAME),
        FULL_NAME,
        EMP_ID
        FROM EMP_TABLE A
    ORDER BY A.FULL_NAME
