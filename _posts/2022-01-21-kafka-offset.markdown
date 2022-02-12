---
layout: post
title:  "Kafka Offset"
date:   2022-01-24 14:15:00 +0100
categories: Kafka
---

On this page we will talk about kafka Offset.

* QueryWatermarkOffsets - Returns a WatermarkOffset which has 2 properties high and low.
* low - the lowest offset available on the offset
* high - this is the End of Partition event on that partition and not the highest offset of a message.
* EnablePartitionEof - set this to true in the consumer config in order to populate property IsPartitionEof on the ConsumeResult.
* without enabling EnablePartitionEof, the IsPartitionEof is always false.
* GetWatermarkOffsets - this method on the consumer relies on local cached offsets in the consumer client.  this is not populated unless Consume() is called by the consumer

It can happen that the committed offset has expired and if you have any piece of logic that relies on checking the last committed offset (by doing _consumer.Committed(TimeSpan)) for eg, then it will return unset.  Unless there is logic to handle this scenario, it will require that the last committed is set to an available offset.  One way to achieve this would be to:
1. Retrieve the low and high offsets by running QueryWatermarketOffsets.
2. Create a TopicPartitionOffset with the low offset - new TopicPartitionOffset(TopicPartition, low)
3. Assign the partition that the offset has to be set on - _consumer.Assign(TopicPartition)
4. Commit the low offset - _consumer.Commit(TopicPartitionOffset);
5. As optional step, can also verify that the committed offset is at the intended offset - _consumer.Committed(TimeSpan)

