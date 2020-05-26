# Topics
- A topic is actually viewed as a partition in Kafka. Each topic has at least one partition
- The order of messages is guaranteed within a partition. The order is not maintained across partitions
- A partition can be consumed by only one consumer of a consumer group. A partition can be consumed by multiple consumer groups
- The number of consumers can not be larger than the number of partitions

## When to use one topic?
- Events that are about the same or similar data entity
- Events that are about the data entities that are often handled together or need to be handled sequentially
- When multiple consumers are consuming from the same set of topics, a subset of this set of topics can probably be combined into one topic. Consuming from Kafka is cheap so it’s okay to consume messages and just ignore the unwanted messages
- It is recommended to start with one topic first. The topic can be gradually split up later since it’s easier to do so than combining several topics into one topic

## References
- https://www.confluent.io/blog/put-several-event-types-kafka-topic/
- https://docs.google.com/document/d/1ZfGJWhlfJf2_EvgHJxsfNbUplqD7JOns1gJ7_rwgeH8/edit?usp=sharing 
