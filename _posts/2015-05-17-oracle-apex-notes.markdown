---
author: guidedmissile
comments: true
date: 2015-05-17 19:26:18+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/05/17/oracle-apex-notes/
slug: oracle-apex-notes
title: Oracle Apex notes
wordpress_id: 283
categories:
- Oracle
tags:
- Oracle Apex
---

Apex Plugins

LinK : http://www.oracle.com/technetwork/developer-tools/apex/application-express/apex-plug-ins-182042.html

Plugins Demo & Links : https://apex.oracle.com/pls/apex/f?p=654321:400:0::NO
- http://apexplained.wordpress.com/2012/08/18/display-loading-image-in-apex/
- http://www.nerd.net.au/24-apex-application-express/report-layout/118-changing-font-size-of-whole-report

To edit existing table template, add below code into page's HTML.
`
.apexir_WORKSHEET_DATA th div {
font: bold 11px/14px "Helvetica Neue",Helvetica,Arial,sans-serif !important;
}
.apexir_WORKSHEET_DATA td {
font: normal 11px/14px "Helvetica Neue",Helvetica,Arial,sans-serif !important;
}`

For classic reports :: Region - """CSS inline"""
`
.t14ReportsRegion th div {
font: bold 11px/14px "Helvetica Neue",Helvetica,Arial,sans-serif !important;
}
.t14ReportsRegion td {
font: normal 11px/14px "Helvetica Neue",Helvetica,Arial,sans-serif !important;
}
`

General page editing settings.
``

.tbody {
margin: 0;
padding: 2cm 0 0 0;
text-align: center;
background-color: black;
font-family: Arial,Helvetica,sans-serif;
color: #cccccc;
font-size: 16pt;
}

.t14ReportsRegion {
min-width:450px;
}

.t14RegionBody {
width: 100%;
}

.t14ReportsRegion th div {
font: bold 11px/14px "Helvetica Neue",Helvetica,Arial,sans-serif !important;
}

.t14ReportsRegion td {
font: normal 11px/14px "Helvetica Neue",Helvetica,Arial,sans-serif !important;
}

.t14Standard {
min-width:450px;
}

.apexir_WORKSHEET_DATA th div {
font: bold 11px/14px "Helvetica Neue",Helvetica,Arial,sans-serif !important;
}
.apexir_WORKSHEET_DATA td {
font: normal 11px/14px "Helvetica Neue",Helvetica,Arial,sans-serif !important;
}

.uReportContainer th div {
font: bold 11px/14px "Helvetica Neue",Helvetica,Arial,sans-serif !important;
}
.uReportContainer td {
font: normal 11px/14px "Helvetica Neue",Helvetica,Arial,sans-serif !important;
}

For colouring the HTML Table report based on column
`
$("td[headers!='column Test']").each(function(){
if(parseInt($(this).text()) > 5){
$(this).css({"background-color":"#FFC000"});
};
if(parseInt($(this).text()) > 15 ){
$(this).css({"background-color":"#FF1919"});
};
});`
