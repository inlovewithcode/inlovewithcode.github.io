---
author: guidedmissile
comments: false
date: 2017-10-28 19:10:23+00:00
layout: page
link: https://inlovewithcode.wordpress.com/hdfs/
slug: hdfs
title: HDFS
wordpress_id: 2482
---

<blockquote>
  > Prefer using full path of the hadoop like `/opt/software/hadoop-2.7.0/bin/hdfs`
</blockquote>



In Hadoop `bin` folder, we do see `hadoop` and `hdfs`. If you are using `hadoop`, we see following request

[code lang=text]
SDS-bash3.2$ hadoop dfs
DEPRECATED: Use of this script to execute hdfs command is deprecated.
Instead use the hdfs command for it.
...
...
[/code]



## basic syntax



[code lang=bash]
hdfs fs [generic options]

    [-help [cmd ...]]
    [-ls [-d] [-h] [-R] [<path> ...]]
    [-mkdir [-p] <path> ...]


    [-chgrp [-R] GROUP PATH...]
    [-chmod [-R] <MODE[,MODE]... | OCTALMODE> PATH...]
    [-chown [-R] [OWNER][:[GROUP]] PATH...]

    [-copyFromLocal [-f] [-p] [-l] ... ]
    [-copyToLocal [-p] [-ignoreCrc] [-crc] ... ]

    [-moveFromLocal ... ]
    [-moveToLocal ]
    [-mv ... ]

    [-df [-h] [<path> ...]]
    [-du [-s] [-h] <path> ...]

    [-rm [-f] [-r|-R] [-skipTrash] ...]
    [-rmdir [--ignore-fail-on-non-empty]

[/code]

Examples

[code lang=bash]
/opt/software/hadoop-2.7.0/bin/hdfs fs -get /hdfs/source/path /tmp/sam/new_folder
/opt/software/hadoop-2.7.0/bin/hdfs fs -copyToLocal /hdfs/source/path /tmp/sam/new_folder
[/code]



## copy files from local



[code lang=bash]
bin/hadoop fs -put /localfs/destination/path /hdfs/source/path
bin/hadoop fs -copyFromLocal /localfs/destination/path /hdfs/source/path 
[/code]



## copy files to local



[code lang=bash]
bin/hadoop fs -get /hdfs/source/path /localfs/destination/path
bin/hadoop fs -copyToLocal /hdfs/source/path /localfs/destination/path
[/code]
