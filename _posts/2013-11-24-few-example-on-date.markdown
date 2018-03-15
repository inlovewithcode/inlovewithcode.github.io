---
author: guidedmissile
comments: true
date: 2013-11-24 13:05:08+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/few-example-on-date/
slug: few-example-on-date
title: Few example on date
wordpress_id: 24
categories:
- Oracle
tags:
- SQL
---

FEW EXAMPLES ON "DATE"

    
    SYSDATE      --GIVES DATE LIKE 12/12/2012
    TO_DATE()    --HELPS TO TEXT TO DATE
    SYSTIMESTAMP --PRINT DATE AND TIME
    
    SELECT TO_CHAR(SYSTIMESTAMP,'MON-YYYY') FROM DUAL;
    
    SELECT * FROM WWV_FLOW_MONTHS_MONTH;
    
    SELECT SYSTIMESTAMP - INTERVAL '10' DAY FROM DUAL;
    
    SELECT SYSDATE-10 FROM DUAL;
    
    SELECT TO_CHAR (SYSDATE+10, 'FMDAY, DDTH MONTH YYYY') FROM DUAL;
    
    BEGIN
    DBMS_OUTPUT.PUT_LINE (
    TO_CHAR (SYSDATE,
    'DAY, DDTH MONTH YYYY',
    'NLS_DATE_LANGUAGE=SPANISH'));
    END;
