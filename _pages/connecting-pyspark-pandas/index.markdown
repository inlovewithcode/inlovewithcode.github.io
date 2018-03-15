---
author: guidedmissile
comments: false
date: 2017-03-27 06:11:21+00:00
excerpt: Basic Data transformation operations in Python Pandas and Apache PySpark.
layout: page
link: https://inlovewithcode.wordpress.com/connecting-pyspark-pandas/
slug: connecting-pyspark-pandas
title: Py - Spark
wordpress_id: 1757
---

![Py Pandas & Apache Dataframes](https://inlovewithcode.files.wordpress.com/2017/03/py-pandas-apache-dataframes1.png)

Here in this tutorial, we shall do a quick & easy lookup of what kind of data operations we can do. If you are familiar with Python Pandas, then these this might be useful for you.

Note:
* this is not introductory session for spark or pandas
* prior understanding of what spark/pandas would be great

We hope you understand/know how to do preprocessing and why it required and how to do ml/why to do and other basic details required for the understanding of this.

For Pyspark, basic requirements like spark content will be loaded by default when you create a notebook. For beginners, you may use following config for starting Pyspark with IPython.

[code lang=text]
PYSPARK_DRIVER_PYTHON=jupyter
PYSPARK_DRIVER_PYTHON_OPTS=notebook

SCALA_HOME=/usr/local/bin/scala
SPARK_HOME=/Users/sampathm/spark2

# PySpark Ipython Notebooks
# https://medium.com/@GalarnykMichael/install-spark-on-mac-pyspark-453f395f240b#.ofy81uj89
clear;
export SPARK_PATH=$SPARK_HOME
export PYSPARK_DRIVER_PYTHON="jupyter"
export PYSPARK_DRIVER_PYTHON_OPTS="notebook"
alias snotebook='$SPARK_PATH/bin/pyspark --master local[2]'

sipy()
{
clear
echo 'Starting Ipython Notebook(PySpark)'
snotebook
}
[/code]

When you want to start PySpark, just type `sipy` in the prompt for "Spark IPython"



### Loading pandas lib



[code lang=python]
import pandas as pd
import numpy as np
[/code]



### Checking Spark



[code lang=python]
# spark context - sc(by default) loaded when we start Ipython Context.
sc
[/code]



### Check Envir & spark versions & files



Inputs:

[code lang=python]
%%sh

# python version
python -V

# pyspark version
pyspark --version

[/code]

Output:

[code lang=shell]
Python 3.5.2 :: Continuum Analytics, Inc.
Welcome to
____ __
/ __/__ ___ _____/ /__
_\ \/ _ \/ _ `/ __/ '_/
/___/ .__/\_,_/_/ /_/\_\ version 2.1.0
/_/

Using Scala version 2.11.8, Java HotSpot(TM) 64-Bit Server VM, 1.8.0_111
Branch
Compiled by user jenkins on 2016-12-16T02:04:48Z
Revision
Url
Type --help for more information.
[/code]



### Load Data



[code lang=python]
# spark
spark_dataframe = spark.read.csv("data.csv", header=True)

# pandas
pd_dataframe = pd.read_csv("data.csv")
[/code]



### Read a sample



[code lang=python]
# spark
print(spark_dataframe.first())

# pandas
print(pd_dataframe.head())
[/code]



### Check columns & data types



[code lang=python]
# spark
spark_dataframe.printSchema()

# pandas
pd_dataframe.dtypes
[/code]



### selection particular columns



[code lang=python]
# spark
spark_dataframe = spark_dataframe.select(['adm', 'ip'])

# pandas
pd_dataframe = pd_dataframe[['ip', 'adm']]
[/code]



### describe a column



[code lang=python]
# spark
spark_dataframe.describe().show()

# pandas
pd_dataframe.describe()
[/code]



### taking a portion of data



[code lang=python]
# spark
spark_dataframe = spark_dataframe.sample(withReplacement=False, fraction=0.10)

# pandas
pd_dataframe = pd_dataframe[:15]
[/code]



### check just columns



[code lang=python]
# pandas
pd_dataframe.columns

# spark
spark_dataframe.columns
[/code]



### column operation



[code lang=python]
# pandas
pd_dataframe.adm = pd_dataframe.adm.apply(lambda x: len(str(x)))

# spark
from pyspark.sql.functions import udf # user definted function
adm_function = udf(lambda x: len(str(x)))
spark_dataframe.withColumn('adm', adm_function(spark_dataframe.adm))
[/code]



### Converting pandas data into spark



[code lang=python]
# spark
pd_spark_dataframe = spark_dataframe.toPandas()

# pandas
spark_pd_dataframe = spark.createDataFrame(dataframe)
[/code]
