# Kafka Cheat Sheet

A simple cheat sheet for Apache Kafka.

## Cluster

A Kafka cluster is a group of brokers that work together to provide a single, highly available, and scalable platform for handling real-time data feeds.

## Broker

A Kafka broker is a server that stores and manages the Kafka topics. Each broker can have zero or more partitions of a topic.

## Topic

A Kafka topic is a category or feed name to which records are published. Topics are always multi-subscriber; that is, a topic can have zero, one, or many consumers that subscribe to the data written to it.

## Partition

A Kafka partition is a unit of parallelism in Kafka. A topic can have one or more partitions. Each partition is an ordered, immutable sequence of records that is continually appended to a structured commit log.

## Leader

The leader of a partition is the node responsible for all reads and writes for the given partition. Each partition has one leader and zero or more followers.

## Record

A record is a key-value pair that is produced by a producer and consumed by a consumer. Records are stored in topics.

## Key

A key is an identifier for a record within a topic. The key is used to decide which partition the record will be written to.

## Value

A value is the data of a record within a topic. The value is the payload of the record.

## Producer

A producer is a process that publishes records to a topic. Producers are responsible for choosing which record to assign to which partition within the topic.

## Consumer

A consumer is a process that subscribes to one or more topics and reads records from the topics. Consumers read records in the order they were produced.

## Consumer Group

A consumer group is a group of consumers that work together to consume records from one or more topics. Each consumer in the group is assigned a subset of the partitions in the topics.

## Offset

An offset is a unique identifier for a record within a partition. Offsets are used to track the progress of a consumer in a partition.

## AVRO / AVSC

AVRO is a data serialization system that provides rich data structures and a compact, fast, binary data format. AVSC is the schema definition language for AVRO.