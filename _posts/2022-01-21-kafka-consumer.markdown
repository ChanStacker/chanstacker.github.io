---
layout: default
title:  "Kafka Consumer"
date:   2022-01-21 12:00:00 +0100
categories: Kafka
---

On this page we wil talk about kafka consumer.

This is here!

1) The Java api allows to consume messages in batches unlike the .NET (Confluent api) which provides a Consume method on the Consumer and return 1 message per consume if available.  This is to mimic the librdkafka API (C/C++) upon which the .NET api is built.
2) A Batchconsumer implementation can easily be implemented with a specified batch size.