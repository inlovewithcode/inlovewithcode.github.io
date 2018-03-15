---
author: guidedmissile
comments: true
date: 2014-01-29 06:49:25+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2014/01/29/notes-on-features-of-oracle-11-g-compression/
slug: notes-on-features-of-oracle-11-g-compression
title: Notes on - Features of oracle 11 G Compression
wordpress_id: 127
categories:
- Oracle
tags:
- 11 G
---

**Oracle Advanced Compression with Oracle Database 11g**

(This is just a short note collected from Oracle : [LINK](http://www.oracle.com/technetwork/database/database-technologies/storage/advanced-compression-whitepaper-130502.pdf))

**OLTP Table Compression**

Oracle’s OLTP Table Compression uses a unique compression algorithm specifically designed to work with OLTP applications. The algorithm works **by eliminating duplicate values within a ****database block, even across multiple columns**. Compressed blocks contain a structure called a **symbol table** that maintains compression metadata. When a block is compressed, **duplicate values ****are eliminated by first adding a single copy of the duplicate value to the symbol table**. Each duplicate value is then replaced by a short reference to the appropriate entry in the symbol table.

Through this innovative design, compressed data is self-contained within the database block as the **metadata used to translate compressed data into its original state is stored in the block**. When compared with competing compression algorithms that maintain a global database symbol table, Oracle’s unique approach offers significant performance benefits by not introducing additional I/O when accessing compressed data

**Migration and Best Practices**

For new tables and partitions, enabling OLTP Table Compression is as easy as simply CREATEing the table or partition and specifying “COMPRESS FOR OLTP”. See the example

Below
<table cellpadding="0" cellspacing="0" border="1" >
<tbody >
<tr >

<td width="620" valign="top" > CREATE TABLE emp (emp_id NUMBER, first_name VARCHAR2(128), last_name VARCHAR2(128)) COMPRESS FOR OLTP;
</td>
</tr>
</tbody>
</table>
For existing tables and partitions, there are three recommended approaches to enabling OLTP

Table Compressions' comparison Table:
<table cellpadding="0" width="619" cellspacing="0" border="1" >
<tbody >
<tr >

<td width="61" valign="top" >S. No.
</td>

<td width="132" valign="top" >Types
</td>

<td width="132" valign="top" >Compression
</td>

<td width="294" valign="top" >Remarks
</td>
</tr>
<tr >

<td width="61" valign="top" >1
</td>

<td width="132" valign="top" >ALTER TABLE … COMPRESS FOR OLTP
</td>

<td width="132" valign="top" >Only for future DML
</td>

<td width="294" valign="top" >
</td>
</tr>
<tr >

<td width="61" valign="top" >2
</td>

<td width="132" valign="top" >Online Redefinition (DBMS_REDEFINITION)
</td>

<td width="132" valign="top" >future DML and alsocompress existing data
</td>

<td width="294" valign="top" >



	
  * For a partitioned Table if you are doing this compress, and at that adding/deletion of a new partition happens #Prob# Indexes will be corrupted and there is a **need to rebuild the indexes.**



</td>
</tr>
<tr >

<td width="61" valign="top" >3
</td>

<td width="132" valign="top" >ALTER TABLE … MOVE COMPRESS FOR OLTP
</td>

<td width="132" valign="top" >future DML and alsocompress existing data
</td>

<td width="294" valign="top" >



	
  * During the activity activity an **exclusive (X) lock is maintained** for writing.

	
  * ALTER TABLE MOVE will **invalidate any indexes on the partition or table**; those **indexes will need to be rebuilt after the ALTER TABLE MOVE.**



</td>
</tr>
</tbody>
</table>
Check this [http://www.oracle.com/technetwork/database/database-technologies/storage/advanced-compression-whitepaper-130502.pdf](http://www.oracle.com/technetwork/database/database-technologies/storage/advanced-compression-whitepaper-130502.pdf) To Know about topics like



	
  * Compression for File Data

	
  * SecureFiles Deduplication

	
  * SecureFiles Compression

	
  * Compression for Backup Data

	
  * Recovery Manager (RMAN) Compression

	
  * Data Pump Compression

	
  * Compression for Network Traffic


review: I personally find this could be very useful, if I have to do application in Oracle APEX.
