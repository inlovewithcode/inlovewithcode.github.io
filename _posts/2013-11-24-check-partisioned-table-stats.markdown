---
author: guidedmissile
comments: true
date: 2013-11-24 01:42:07+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/11/24/check-partisioned-table-stats/
slug: check-partisioned-table-stats
title: Check Partisioned table stats
wordpress_id: 11
---

Checks partisioned tables satatistics

    
    select substr(table_name,1,20) partitioned_table,
        substr(column_name,1,20) key_column,
        count(*) no_stats,
        count(*)/total_partitions*100 "NO_STAT%"
    from (
        select table_name,
            column_name,
            partition_name,
            low_value,
            count(*) over (partition by table_name, column_name)
            total_partitions
        from user_part_col_statistics
        where (table_name,column_name) in
            (select name,column_name
            from user_part_key_columns
            where object_type = 'TABLE')
        )
    where low_value is null
        group by table_name,
        column_name,
        total_partitions
    
