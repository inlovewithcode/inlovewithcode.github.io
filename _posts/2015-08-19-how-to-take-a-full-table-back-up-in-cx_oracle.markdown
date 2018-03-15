---
author: guidedmissile
comments: true
date: 2015-08-19 09:10:20+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/08/19/how-to-take-a-full-table-back-up-in-cx_oracle/
slug: how-to-take-a-full-table-back-up-in-cx_oracle
title: How to take a full table back-up in Cx_Oracle?
wordpress_id: 594
categories:
- Oracle
- Python
---

Here is a python script written for you to take a back of all tables information. As you might be only required to take back-up specific table(s) you can tweek below line from code

    
    <span class="n">sql</span> <span class="o">=</span> <span class="s">"select * from tab"</span> <span class="c"># get a list of all tables</span>


** Code:**

    
    <span class="c"># Export Oracle database tables to CSV files</span>
    <span class="c"># FB36 - 201007117</span>
    
    <span class="k">import</span> <span class="nn">sys</span>
    <span class="k">import</span> <span class="nn">csv</span>
    <span class="k">import</span> <span class="nn">cx_Oracle</span>
    
    <span class="n">connection</span> <span class="o">=</span> <span class="nb">raw_input</span><span class="p">(</span><span class="s">"Enter Oracle DB connection (uid/pwd@database) : "</span><span class="p">)</span>
    <span class="n">orcl</span> <span class="o">=</span> <span class="n">cx_Oracle</span><span class="o">.</span><span class="n">connect</span><span class="p">(</span><span class="n">connection</span><span class="p">)</span>
    <span class="n">curs</span> <span class="o">=</span> <span class="n">orcl</span><span class="o">.</span><span class="n">cursor</span><span class="p">()</span>
    
    <span class="n">printHeader</span> <span class="o">=</span> <span class="bp">True</span> <span class="c"># include column headers in each table output</span>
    
    <span class="n">sql</span> <span class="o">=</span> <span class="s">"select * from tab"</span> <span class="c"># get a list of all tables</span>
    <span class="n">curs</span><span class="o">.</span><span class="n">execute</span><span class="p">(</span><span class="n">sql</span><span class="p">)</span>
    
    <span class="k">for</span> <span class="n">row_data</span> <span class="ow">in</span> <span class="n">curs</span><span class="p">:</span>
        <span class="k">if</span> <span class="ow">not</span> <span class="n">row_data</span><span class="p">[</span><span class="mf">0</span><span class="p">]</span><span class="o">.</span><span class="n">startswith</span><span class="p">(</span><span class="s">'BIN$'</span><span class="p">):</span> <span class="c"># skip recycle bin tables</span>
            <span class="n">tableName</span> <span class="o">=</span> <span class="n">row_data</span><span class="p">[</span><span class="mf">0</span><span class="p">]</span>
    
            <span class="c"># output each table content to a separate CSV file</span>
            <span class="n">csv_file_dest</span> <span class="o">=</span> <span class="n">tableName</span> <span class="o">+</span> <span class="s">".csv"</span>
            <span class="n">outputFile</span> <span class="o">=</span> <span class="nb">open</span><span class="p">(</span><span class="n">csv_file_dest</span><span class="p">,</span><span class="s">'w'</span><span class="p">)</span> <span class="c"># 'wb'</span>
            <span class="n">output</span> <span class="o">=</span> <span class="n">csv</span><span class="o">.</span><span class="n">writer</span><span class="p">(</span><span class="n">outputFile</span><span class="p">,</span> <span class="n">dialect</span><span class="o">=</span><span class="s">'excel'</span><span class="p">)</span>
            <span class="n">sql</span> <span class="o">=</span> <span class="s">"select * from "</span> <span class="o">+</span> <span class="n">tableName</span>
            <span class="n">curs2</span> <span class="o">=</span> <span class="n">orcl</span><span class="o">.</span><span class="n">cursor</span><span class="p">()</span>
            <span class="n">curs2</span><span class="o">.</span><span class="n">execute</span><span class="p">(</span><span class="n">sql</span><span class="p">)</span>
    
            <span class="k">if</span> <span class="n">printHeader</span><span class="p">:</span> <span class="c"># add column headers if requested</span>
                <span class="n">cols</span> <span class="o">=</span> <span class="p">[]</span>
                <span class="k">for</span> <span class="n">col</span> <span class="ow">in</span> <span class="n">curs2</span><span class="o">.</span><span class="n">description</span><span class="p">:</span>
                    <span class="n">cols</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">col</span><span class="p">[</span><span class="mf">0</span><span class="p">])</span>
                <span class="n">output</span><span class="o">.</span><span class="n">writerow</span><span class="p">(</span><span class="n">cols</span><span class="p">)</span>
    
            <span class="k">for</span> <span class="n">row_data</span> <span class="ow">in</span> <span class="n">curs2</span><span class="p">:</span> <span class="c"># add table rows</span>
                <span class="n">output</span><span class="o">.</span><span class="n">writerow</span><span class="p">(</span><span class="n">row_data</span><span class="p">)</span>
    
            <span class="n">outputFile</span><span class="o">.</span><span class="n">close</span><span class="p">()
    </span>


Source: http://code.activestate.com/recipes/577304-export-oracle-database-to-csv-using-cx_oracle/

Golden Rule : Don't re-invent the wheel.
