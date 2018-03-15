---
author: guidedmissile
comments: false
date: 2017-08-22 05:43:58+00:00
layout: page
link: https://inlovewithcode.wordpress.com/logstash-plugin-alternate-for-xlsx-mysql/
slug: logstash-plugin-alternate-for-xlsx-mysql
title: Logstash Plugin alternate for XLSX, MYSQL
wordpress_id: 2416
---

As you might have already known, logstash does not provide a plugin for uploading data to MySql or parsing Xlsx files. So, I have coded some generic tools for doing so.

They are not very perfect solutions as you might expect but nonetheless, if they are working as expected then it should not be a problem.

We are using `logstash-input-exec` for doing this work.

For XLSX, we are actually writing a converter to CSV. As logstash provide CSV support, we want to reduce the coding to minimal and provide a solution.

So if your goal is

[code lang=text]
XSLX(LOGSTASH INPUT) --> << file processing >> --> (LOGSTASH OUTPUT)
[/code]

we are breaking it down to following

[code lang=text]
XSLX(LOGSTASH INPUT) --> [[ << external input triger >> --> (CSV OUTPUT) ]]]
CSV(LOGSTASH INPUT) --> << file processing >> --> (LOGSTASH OUTPUT)
[/code]

Similarly, for to upload data to MySql.

[code lang=text]
(LOGSTASH INPUT) --> << file processing >> --> (LOGSTASH OUTPUT)MySQL
[/code]

We are breaking it down to following

[code lang=text]
(LOGSTASH INPUT) --> << file processing >> --> (LOGSTASH OUTPUT)CSV
CSV(LOGSTASH INPUT) --> [[ << external input triger >> --> (LOGSTASH OUTPUT) ]]
[/code]

Please check my GitHub page for repo.
