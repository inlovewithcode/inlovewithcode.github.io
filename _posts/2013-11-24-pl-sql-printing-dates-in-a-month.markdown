---
author: guidedmissile
comments: true
date: 2013-11-24 09:44:47+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/pl-sql-printing-dates-in-a-month/
slug: pl-sql-printing-dates-in-a-month
title: PL SQL Printing Dates in a Month
wordpress_id: 18
categories:
- Oracle
tags:
- SQL
---

-- anonymous block to print of dates in a month

    
    
    declare
     som date; --start of month
     eom date; --end of month
     tmp date;
    begin
     select last_day(add_months(sysdate,-1))+1 into som from dual; --#current som
     select last_day(sysdate) into eom from dual;
    
     htp.print(TO_CHAR(SOM, 'FMDay, DDth Month YYYY'));
     tmp := som;
     while tmp < eom
      loop
       if lower(to_char(tmp,'FMDay')) = lower('sunday') then htp.print('-------------------------'); end if;
       tmp := tmp +1;
       htp.print(TO_CHAR(TMP, 'FMDay, DDth Month YYYY'));
      end loop;
    end;
