---
author: guidedmissile
comments: true
date: 2013-11-24 13:19:12+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/automation-backup-script/
slug: automation-backup-script
title: AUTOMATION BACKUP SCRIPT
wordpress_id: 32
categories:
- Oracle
tags:
- SQL
---

It is often a nice to create a set object with Prefix/ Suffix, if so then with below procedure its easy to get **all objects source** codes in one go.

    
    BEGIN
    FOR C IN (SELECT UNIQUE NAME FROM USER_SOURCE WHERE NAME LIKE '%app_prefix or app_suffix%')
    LOOP
      HTP.PRINT('----------------------------' || C.NAME || '----' );
     FOR D IN (SELECT TEXT FROM USER_SOURCE WHERE NAME = C.NAME ORDER BY LINE)
      LOOP
       HTP.PRINT(D.TEXT);
      END LOOP;
    END LOOP;
    END;
