---
layout: post
title:  "Kafka Producer"
date:   2022-01-21 12:00:00 +0100
categories: Kafka
---

Creating a kafka producer can be as simple as the code below:

{% highlight csharp linenos %}
static void Produce(string topic, ClientConfig config)
{
    using (var producer = new ProducerBuilder<string, string>(config).Build())
    {
        int numProduced = 0;
        int numMessages = 10;
        for (int i=0; i<numMessages; ++i)
        {
            var key = "alice";
            var val = JObject.FromObject(new { count = i }).ToString(Formatting.None);

            Console.WriteLine($"Producing record: {key} {val}");

            producer.Produce(topic, new Message<string, string> { Key = key, Value = val },
                (deliveryReport) =>
                {
                    if (deliveryReport.Error.Code != ErrorCode.NoError)
                    {
                        Console.WriteLine($"Failed to deliver message: {deliveryReport.Error.Reason}");
                    }
                    else
                    {
                        Console.WriteLine($"Produced message to: {deliveryReport.TopicPartitionOffset}");
                        numProduced += 1;
                    }
                });
        }

        producer.Flush(TimeSpan.FromSeconds(10));

        Console.WriteLine($"{numProduced} messages were produced to topic {topic}");
    }
}
{% endhighlight %}