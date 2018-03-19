---
author: guidedmissile
comments: false
date: 2017-05-03 10:25:27+00:00
layout: page
link: https://inlovewithcode.wordpress.com/data-analaysis/r/
slug: r
title: R
wordpress_id: 2114
---

#### R Beginners Functions



R is another open source programmer language, inspired from S language which was written for Statistician who wanted to do Data Analytics and Data Science.

Here are some beginner functions you can use to write start working with.





  * `getwd()` to check there current working directory


  * `setwd("~/Desktop/")` to change the current working directory location


  * `dir()` to check the files in that directory.


  * `c` or `array` fns to create an array


  * `rbind` to combine two arrays


  * `sort` to sort values


  * `seq` to generate numbers in a range(range fns in Python)


  * `which.max` returns the index of the max element in the array


  * `data.frame` to create a data frame from arrays


  * `read.csv` to create a data frame from csv


  * `write.csv(WHO_Europe, "WHO_Europe.csv”)` to save the file


  * `match` is like a counting no.of times a value occurred in a column


  * `as.numeric` to convert boolean/logical operator values to numeric



**some constants**





  * NA : Not Available (i.e. missing values)


  * NaN : Not a Number (e.g. 0/0)


  * Inf: Infinity


  * -Inf : Minus Infinity.



**dataframe**





  * `names` to print all the column names in a data frame


  * `$` to check a data frame each column’s values


  * `dim` to check the shape of the data frame


  * `str` to check the structure/type of object/variable


  * `summary` to check summary of data frame


  * `subset` to filter the required data.


  * `table` is like summary of a categorical variables


  * `tapply(WHO$Over60, WHO$Region, max)` is like pivot


  * `tapply(WHO$LiteracyRate, WHO$Region, max, na.rm=TRUE)` excluding the NA's



**Check/remove Locals variables**





  * `ls()` to check all local variables


  * `rm(..)` to remove variables



__Plotting __



  * `hist` to do histogram plots


  * `plot` for scatter plots/ linear plots


  * `boxplot(WHO$LifeExpectancy ~ WHO$Region)` to box plot Life Expectancy for each region



    * internal optional labels are `xlab`, `ylab`, `name`





**Date/Format**





  * `as.Date(strptime(, "%m/%d/%y %H:%M”))` to convert string into Date Type


  * `format` to convert strings into string



BUILT-IN FUNCTION



  * http://www.statmethods.net/management/functions.html



EXAMPLES:



  * https://en.wikibooks.org/wiki/R_Programming/Sample_Session



MAP, REDUCE, FILTER, FIND, NEGATE:



  * http://www.johnmyleswhite.com/notebook/2010/09/23/higher-order-functions-in-r/



Sample Data Files:



  * https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/ccdc87b80d92a9c24de2f04daec5bb58/asset-v1:MITx+15.071x_3+1T2016+type@asset+block/WHO.csv


  * https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/3ef78a720083c74cd2649289a475158d/asset-v1:MITx+15.071x_3+1T2016+type@asset+block/USDA.csv


