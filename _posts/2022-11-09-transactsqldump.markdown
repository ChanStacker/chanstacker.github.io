---
layout: post
title: "Transact SQL Dump"
date: 2022-11-15 22:00:00 +0100
categories: SqlServer
---

* T-SQL is Microsoft's implementation of SQL with a whole bunch of additional features and functions on top.

* Start of month date - `DATEADD(m, DATEDIFF(m, 0, @CurrentDate), 0)`
* Start of Year date - `DATEADD(yy, DATEDIFF(yy, 0, @CurrentDate), 0)`
* CTE 
{% highlight sql linenos%}
;WITH cteName AS 
(Select ...),
cteName2 AS
(Select ...)
Select * from cteName2
{% endhighlight %}
