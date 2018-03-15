---
author: guidedmissile
comments: true
date: 2013-11-24 13:15:53+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/fetch-a-procedure-definition/
slug: fetch-a-procedure-definition
title: FETCH A PROCEDURE DEFINITION
wordpress_id: 30
categories:
- Oracle
tags:
- SQL
---

HOW TO FETCH A PROCEDURE DEFINITION

    
    
    SELECT TEXT FROM USER_SOURCE WHERE TYPE = 'PROCEDURE' AND NAME = PROCEDURE_NAME;
    
    -- EXAMPLE
    SELECT DBMS_METADATA.GET_DDL('TABLE','EMP_TABLE') FROM DUAL;
    SELECT DBMS_METADATA.GET_DDL('PROCEDURE','EMP_DETAILS_PROC') FROM DUAL;
    
    SELECT TEXT 
    FROM USER_SOURCE 
     WHERE NAME IN ('application_func_name_here') 
     ORDER BY LINE; -- order is very important
    
