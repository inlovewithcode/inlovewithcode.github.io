---
author: guidedmissile
comments: false
date: 2015-10-20 11:35:21+00:00
layout: page
link: https://inlovewithcode.wordpress.com/plsql/sql/
slug: sql
title: SQL
wordpress_id: 649
---

# Tips on Oracle SQL


How to get date/month/year from a date column?


<blockquote>`SELECT EXTRACT(month FROM order_date) "Month",
COUNT(order_date) "No. of Orders"
FROM orders
GROUP BY EXTRACT(month FROM order_date)
ORDER BY "No. of Orders" DESC;`</blockquote>


Source :[Click Here](http://docs.oracle.com/cd/B19306_01/server.102/b14200/functions050.htm)

