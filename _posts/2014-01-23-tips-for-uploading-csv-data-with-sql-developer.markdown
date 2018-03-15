---
author: guidedmissile
comments: true
date: 2014-01-23 11:34:36+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2014/01/23/tips-for-uploading-csv-data-with-sql-developer/
slug: tips-for-uploading-csv-data-with-sql-developer
title: Tips for uploading csv data with sql developer
wordpress_id: 102
categories:
- Oracle
tags:
- Data upload
- SQL Developer
---

Use Sql developer 4.0 with pre-installed Java, this will help you for good extend.

Q: How to upload data to table ?
Ans: From Sql Developer, select the required table and check for "Import". After that, flow with the flow ;)

If you are trying upload csv file using in-built tools, few things



	
  1. Which important Data, make sure you set you upload max rows and display rows in limit.(Max rows to be uploaded should > rows in you csv file)

	
  2. Note - if any **Date** characters are there, make sure to give date format of column "DD-MON-YYY" for '14-APR-2006' ( This is in the export process, -@ 4th stage, make sure you test it before upload)

	
  3. 

If you are trying to upload data as insert - Sql format, you remember the follow

	
  1. "SET SCAN OFF", To prevent system asking you for entering values. If sql querying is having any '&', It will think that we are going to input something there.

	
  2. "Set NOLOG", only if you are sure.In case of csv import with built-in tools of sql developer - you don't need to bother much.

	
  3. Commit, after 2 ~ 3k records, to be safer side if you are expecting any chances of errors.


