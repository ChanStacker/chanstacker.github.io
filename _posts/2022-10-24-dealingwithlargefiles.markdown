---
layout: post
title:  "Dealing with large files"
date:   2022-10-24 09:00:00 +0100
categories: .Net
---

* Classifying a file as "large" is very much a relative thing.  It depends on the amount of resources available on the machine as well as the internet bandwidth in case the file is being loaded from the network.  
* In any case, once a file is deemed large for the current context, there are several concerns to bear in mind when processing such a file.  Fortunately there exists several techniques explorer over many years about how to handle large files.  