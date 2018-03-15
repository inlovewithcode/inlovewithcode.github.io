---
author: guidedmissile
comments: true
date: 2015-05-18 06:50:49+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/05/18/generating-html-tables-with-totals/
slug: generating-html-tables-with-totals
title: Generating HTML tables with totals
wordpress_id: 90
categories:
- Oracle
- Python
post_format:
- Audio
tags:
- Oracle Apex
---

Got sick of finding a solution to creating a table with totals,.. I made this tool to fix it up.



    
    # 
    #!/bin/python
    
    """
    DESCRIPTION: Provides html code for db table/query with totals
    
    RULES:
     ALWAYS UPDATE FOLLOWING 3 AT ONCE !
     - QUERIES
     - QUERIES_HEADERS
     - QUERY_HTML_DATA_HEADINGS
    
    PARSING OPTIONS:
     Please check for parse options as below
     Example
     $python -h
    """
    
    __version__ = "1.0"
    
    import os
    import csv
    import cx_Oracle
    from optparse import OptionParser
    
    # Database Credentials
    USERNAME = ""
    PASSWORD = ""
    
    ORA_HOST = ""
    PORT = 1522
    SID = ""
    DSN_TNS = cx_Oracle.makedsn(ORA_HOST, PORT, SID)
    
    QUERIES = ["""select Item_name,
     item_quanity,
     item_unit_cost,
     item_quanity*item_unit_cost as cost
     from billings
     ""","""select Item_name,
     item_quanity,
     item_unit_cost,
     item_quanity*item_unit_cost as cost
     from billings
     ""","""select Item_name,
     item_quanity,
     item_unit_cost,
     item_quanity*item_unit_cost as cost
     from billings
     """]
    
    # HEADING ROW FOR HTML TABLE
    
    QUERIES_HEADERS = [ """
    
     ITEM NAMEQUANTITYUNIT PRICEPRICE
     """, """
    
     ITEM NAMEQUANTITYUNIT PRICEPRICE
     """, """
    
     ITEM NAMEQUANTITYUNIT PRICEPRICE
     """]
    
    QUERY_HTML_DATA_HEADINGS = ["""
     SALES UNIT PRICE
     """, """
    
    
     SALES UNIT PRICE 
    
     """, """
    
    
     SALES UNIT PRICE 
    
     """]
    
    HTML_HEADER = """
    
     table.custom_table_css { padding: 15px;
     margin-left:4px;empty-cells: show;
     font-family: verdana, arial, sans-serif;
     font-size: 12px; color: rgb(51, 51, 51);
     border-width: 1px; border-color: rgb(102, 102, 102);
     border-collapse: collapse;
     background-color: rgb(255, 255, 255);}
    
     table.custom_table_css tr { }
    
     table.custom_table_css th { border: 1px solid rgb(102, 102, 102);
     padding: 9px;vertical-align: top;
     background-color: rgb(222, 222, 222); wraps; }
    
     table.custom_table_css td { border: 1px solid rgb(102, 102, 102);
     padding: 8px;vertical-align: bottom; }
    
     """
    
    HTML_TABLE_OPEN = """ """
    
    HTML_TABLE_CLOSE = "\n\n"
    
    HTML_FOOTER = ""
    
    # HTML TAGGERS - with css details
    
    ### CONFIGURATIONS [ENDS]
    
    def get_querydata(queries):
    """RUNS LIST OF QUERIES & GETS STATUS**"""
     connection = cx_Oracle.connect(USERNAME, PASSWORD, DSN_TNS)
     cursor = connection.cursor()
     data = []
     for each in queries:
     data.append(cursor.execute(each).fetchall())
     cursor.close()
     connection.close()
     return data;
    
    def dress_rawdata_row(row):
     """ Row is converted to Html row format
     & last column is aligned to right """
     table_row = ""
     for each in row:
     if row.index(each) == len(row) -1 :
     table_row = table_row + "\t"
     table_row = table_row + str(each) + "\n"
     else :
     table_row = table_row + "\t" + str(each) + "\n"
     table_row = "\n" + table_row + "\n"
    return table_row
    
    def dress_rawdata(raw_tabdata):
     """ to convert a simple raw format row
     (vector or list) to HTML format rows
     along with extra -> TOTALS ROW"""
     html_table_container = []
     for i in range(len(raw_tabdata)):
     data = []
     table_total_value = 0
     data.append("")
     # feching table header def from QUERIES_HEADERS
     data.append( QUERIES_HEADERS[i]);
     for row in raw_tabdata[i]:
     table_total_value = table_total_value + int(row[-1])
     data.append(dress_rawdata_row(row))
     if len(raw_tabdata[i]) > 0 :
     # setting-up totals row
     totals_row = [ "" for each1 in row ]
     totals_row[-2] = "Total"
     totals_row[-1] = "%r" % table_total_value
     data.append(dress_rawdata_row(totals_row))
     html_table_container.append(data)
     return html_table_container
    
    def writetofile(data,filename):
     """inputdata to given filename"""
     fp = open(filename,"w")
     fp.writelines(data)
     fp.close()
    
    def main():
     """ Fetches data & send email """
     query_result = get_querydata(QUERIES)
    
     html_table_container = dress_rawdata(query_result)
    
     html_data = ""
     html_data = html_data + "\n\n" + HTML_HEADER
     for i in range(len(html_table_container)):
     html_data = html_data + QUERY_HTML_DATA_HEADINGS[i]
     html_data = html_data + HTML_TABLE_OPEN
     html_data = html_data + "\n".join(html_table_container[i])
     html_data = html_data + HTML_TABLE_CLOSE
     html_data = html_data + "\n\n" + HTML_FOOTER
     return html_data
    
    
    
    parser = OptionParser()
    parser.add_option("-f", "--file", dest="filename",
    help="saves report to input file", metavar="FILE")
    (options, args) = parser.parse_args()
    
    filename = str(options.filename)
    
    if filename == "None":
    print "\nNo filname is provided !"
    else :
    writetofile( main(), filename);
    print "\nHTML Mail is stored in file named :", filename
    
    
    








