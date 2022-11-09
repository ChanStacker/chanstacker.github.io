---
layout: post
title: "SQL Server Performance Tuning"
date: 2022-11-09 09:00:00 +0100
categories: Azure
---

* There are 2 ways by which the query engine retrieves data: Table scan or Index
* Table Scan - the query engine goes through every row of the table from the beginning and add the ones that match to the search criteria to the result set.  Table scan can be quite efficient if the table is small but gets expensive as the table grows.
* Index Scan - the query engine performs an index scan when there is a clustered index present and no constraint on the search criteria eg without a WHERE clause.  This scan takes advantage of the b-tree structure and retrieves data in a sorted manner.
* Index Seek - the query engine performs an index seek when it can retrieve specific rows based on a search condition.  It is the fastest way of retrieving data.
* Ctrl + A - to bring up the execution plan in SSMS
