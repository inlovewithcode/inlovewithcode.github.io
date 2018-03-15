---
author: guidedmissile
comments: false
date: 2015-10-20 11:10:04+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/10/20/parsing-datetime-in-python/
slug: parsing-datetime-in-python
title: Parsing datetime in Python..?
wordpress_id: 644
categories:
- Python
---

Parsing datetime in Python..?

As @TimPietzcker suggested, the dateutil package is the way to go, it handles the first 3 formats correctly and automatically:


<blockquote>`>> from dateutil.parser import parse
>>> parse("Fri Sep 25 18:09:49 -0500 2009")
datetime.datetime(2009, 9, 25, 18, 9, 49, tzinfo=tzoffset(None, -18000))
>>> parse("2008-06-29T00:42:18.000Z")
datetime.datetime(2008, 6, 29, 0, 42, 18, tzinfo=tzutc())
>>> parse("2011-07-16T21:46:39Z")
datetime.datetime(2011, 7, 16, 21, 46, 39, tzinfo=tzutc())`</blockquote>


The unixtime format it seems to hick up on, but luckily the standard datetime.datetime is up for the task:


#### Converting Unixtime




<blockquote>`>> from datetime import datetime
>>> datetime.utcfromtimestamp(float("1294989360"))
datetime.datetime(2011, 1, 14, 7, 16)`</blockquote>


It is rather easy to make a function out of this that handles all 4 formats:



<blockquote>`from dateutil.parser import parse
from datetime import datetime

def parse_time(s):
try:
ret = parse(s)
except ValueError:
ret = datetime.utcfromtimestamp(s)
return ret`</blockquote>



source: http://stackoverflow.com/questions/27804057/concise-ascii-date-to-decimal-date
