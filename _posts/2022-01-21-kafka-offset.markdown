---
layout: post
title:  "Kafka Offset"
date:   2022-01-24 14:15:00 +0100
categories: Kafka
---

On this page we wil talk about kafka Offset.

* QueryWatermarkOffsets - Returns a WatermarkOffset which has 2 properties high and low.
* low - the lowest offset available on the offset
* high - this is the End of Partition event on that partition and not the highest offset of a message.
* EnablePartitionEof - set this to true in the consumer config in order to populate property IsPartitionEof on the ConsumeResult.
* without enabling EnablePartitionEof, the IsPartitionEof is always false.
* GetWatermarkOffsets - this method on the consumer relies on local cached offsets in the consumer client.  this is not populated unless Consume() is called by the consumer
