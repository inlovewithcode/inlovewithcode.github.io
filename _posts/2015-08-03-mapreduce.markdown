---
author: guidedmissile
comments: true
date: 2015-08-03 09:20:49+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2015/08/03/mapreduce/
slug: mapreduce
title: Map Reduce
wordpress_id: 494
tags:
- Algorithms
- MapReduce
---

The "MapReduce System" orchestrates the processing by **marshalling(1)** the distributed servers, running the various tasks in parallel, managing all communications and data transfers between the various parts of the system, and providing for **redundancy(2)** and **fault tolerance**(3).

**Keywords:** Marshalling, Parallel processing, Distributes systems, Redundancy and Fault Tolerance

To "**marshal**" an object means to record its state and codebase(s) in such a way that when the marshalled object is "unmarshalled", a copy of the original object is obtained, possibly by automatically loading the class definitions of the object. You can marshal any object that is serializable or remote. Marshalling is like serialization, except marshalling also records codebases. Marshalling is different from serialization in that marshalling treats remote objects specially

**Fault tolerance example**, the Transmission Control Protocol (TCP) is designed to allow reliable two-way communication in a packet-switched network, even in the presence of communications links which are imperfect or overloaded.

[![MAP-REDUCE](https://inlovewithcode.files.wordpress.com/2015/08/map-reduce.jpg)](https://inlovewithcode.files.wordpress.com/2015/08/map-reduce.jpg)

The model is inspired by the map and reduce functions commonly used in **functional programming**, although their purpose in the MapReduce framework is not the same as in their original forms.





  *  The key contributions of the MapReduce framework are not the actual **map** and **reduce** functions, but the **scalability** and **fault-tolerance** achieved for a variety of applications by **optimizing** the execution engine once.



[![MAP-REDUCE(02)](https://inlovewithcode.files.wordpress.com/2015/08/map-reduce02.jpg)](https://inlovewithcode.files.wordpress.com/2015/08/map-reduce02.jpg)





  * As such, **a single-threaded implementation of MapReduce (such as MongoDB) will usually not be faster** than a traditional (non-MapReduce) implementation, **any gains are usually only seen with multi-threaded implementations**.[8]



The use of this model is beneficial only when the optimized distributed shuffle operation (which reduces network communication cost) and fault tolerance features of the MapReduce framework come into play. **Optimizing the communication cost is essential to a good MapReduce algorithm**.

Further Learning Sources:




    
  * [http://www.tutorialspoint.com/hadoop/hadoop_mapreduce.htm](http://www.tutorialspoint.com/hadoop/hadoop_mapreduce.htm)

    
  * [http://bigdatauniversity.com/bdu-wp/bdu-course/hadoop-fundamentals-i-version-3/](http://bigdatauniversity.com/bdu-wp/bdu-course/hadoop-fundamentals-i-version-3/)



Article Source:


    
  *  [https://en.wikipedia.org/wiki/MapReduce](https://en.wikipedia.org/wiki/MapReduce)


