---
author: guidedmissile
comments: true
date: 2017-03-11 05:23:43+00:00
excerpt: Using Apache Spark 2.1, Scala 2.12 &amp; Sbt 0.13 build a Simple App for
  a quick start on Spark Scala
layout: post
link: https://inlovewithcode.wordpress.com/2017/03/11/spark-simple-app-with-sbt-config-sbt-assembly-some-time-saving-advice/
slug: spark-simple-app-with-sbt-config-sbt-assembly-some-time-saving-advice
title: Spark - Simple App with  SBT Config, SBT Assembly & some time saving advice
wordpress_id: 1693
categories:
- DS
post_format:
- Aside
---

SBT is an acronym for Simple Build Tool, used for building tools(used for build structure, config management, library management, documentation, and so on). Please check [here](http://www.scala-sbt.org/) for more details.

Goal of this post is to provide you a basic `build.sbt` config and a simple script for testing install Spark.

I have already set up a Spark(Spark 2.1.0 built for Hadoop 2.7.3) on Mac OS X El Capiton - 10.11.6



## Brew Installations



If you are a mac user like me, you can use `brew` to install `scala` & `sbt`.

[code lang=text]
SDS-bash3.2$ javac -version
javac 1.8.0_111
[/code]



## Scala Details



[code lang=text]
Scala code runner version 2.12.1 -- Copyright 2002-2016, LAMP/EPFL and Lightbend, Inc.
SDS-bash3.2$
[/code]



## Spark Details



[code lang=text]
SDS-bash3.2$ sparkR --version
Welcome to
____ __
/ __/__ ___ _____/ /__
_\ \/ _ \/ _ `/ __/ '_/
/___/ .__/\_,_/_/ /_/\_\ version 2.1.0
/_/

Using Scala version 2.11.8, Java HotSpot(TM) 64-Bit Server VM, 1.8.0_111
Branch
Compiled by user jenkins on 2016-12-16T02:04:48Z
[/code]



## SBT Config for Spark Project



File: build.sbt

[code lang=text]
name := "hello"

version := "1.0"

scalaVersion := "2.11.7"

logLevel := Level.Error

organization := "sampath.sbt.hello"

logLevel := Level.Error

libraryDependencies ++= Seq(
"org.apache.spark" % "spark-core_2.11" % "2.1.0",
"org.apache.spark" % "spark-sql_2.11" % "2.1.0",
"org.apache.spark" % "spark-mllib_2.11" % "2.1.0" withSources()
)
[/code]



## Test run with Spark



File: SimpleApp.scala

[code lang=text]
import org.apache.spark.SparkContext
import org.apache.spark.SparkContext._
import org.apache.spark.SparkConf

object TextFileOp extends Serializable {
def filterAB(sc: SparkContext) = {
val logFile = "build.sbt" // Should be some file on your system
val logData = sc.textFile(logFile, 2).cache()
val numAs = logData.filter(line => line.contains("a")).count()
val numBs = logData.filter(line => line.contains("b")).count()
println("===================\n\n")
println(s"Lines with a: $numAs, Lines with b: $numBs")
println("===================\n\n")
}
}

object SimpleApp {
def main(args: Array[String]) {

val conf = new SparkConf()
.setAppName("Simple Application")
.setMaster("local[2]")
val sc = new SparkContext(conf)
TextFileOp.filterAB(sc)
sc.stop()
}
}
[/code]



## SBT Amendments for SBT Assembly



File: build.sbt

[code lang=text]
name := "hello"

version := "1.0"

scalaVersion := "2.11.7"

logLevel := Level.Error

organization := "sampath.sbt.hello"

logLevel := Level.Error

libraryDependencies ++= Seq(
"org.apache.spark" % "spark-core_2.11" % "2.1.0" % "provided", // changed
"org.apache.spark" % "spark-sql_2.11" % "2.1.0",
"org.apache.spark" % "spark-mllib_2.11" % "2.1.0" withSources()
)

// To handle decoupling issues

assemblyMergeStrategy in assembly := {
case PathList("jj2000", "j2k", xs @_*) => MergeStrategy.first
case x =>
val oldStrategy = (assemblyMergeStrategy in assembly).value
oldStrategy(x)
}

assemblyMergeStrategy in assembly := {
case PathList("META-INF", xs @ _*) => MergeStrategy.discard
case x => MergeStrategy.first
}
[/code]

File: project.plugins.sbt

[code lang=text]
<br />addSbtPlugin("com.eed3si9n" % "sbt-assembly" % "0.14.4")

addSbtPlugin("net.virtual-void" % "sbt-dependency-graph" % "0.8.2")
[/code]



## Best Advices:







  * Major & Minors Version do make their differences. Be mindful while installations.


  * Stick to official websites for adding configuration like above plugins.


