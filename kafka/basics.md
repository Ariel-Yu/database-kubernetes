# Kafka basics
- [Producer](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kafka/basics.md#producer)
- [Broker](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kafka/basics.md#broker)
- [Consumer](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kafka/basics.md#consumer)
- [Topic](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kafka/basics.md#topic)
- [Partition](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kafka/basics.md#partition)
- [Data element](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kafka/basics.md#data-element-recordmessageevent)
- [Zookeeper](https://github.com/Ariel-Yu/knowledge-bases/blob/master/kafka/basics.md#zookeeper)

## Producer
- Producers are systems that are responsible for producing data into Kafka brokers
- A producer can write to many topics/partitions/brokers

## Broker
- Brokers are usually built as a cluster
- Brokers will send back **acknowlegement** upon successfully or **nagative acknowledgement** upon unsuccessfully receiving data from producers
- Data is stored in the local storage on the brockers

## Consumer
- Consumers are systems that consume data from the kafka brokers
- Consumers can read from many topics/partitions/brokers

## Topic
- Each topic can have multiple partitions to enable higher throughput and lowever latency
- Each topic has an retention time defined to indicate how long the data may live in Kafka

## Partition
- Each partition can have multiple segments depends on the size of the data to enable optimization of I/O
- Partitions of the same topic may live on different brokers
- Purposes of partitions
  - Load balancing
  - Semantic partitioning
- Partition policies
  - Default: hash(key) % (# of partitions)
  - Without key: Round-Robin
  
## Data element (record/message/event)
- Header (metadata)
  - Topic
  - Partition
  - Timestamp
- Body
  - Key
  - Value

## Zookeeper  
- Cluster management
- Failure detection and recovery
- Store ACLs and screts
- An ensemble is usually formed by 3~5 servers
