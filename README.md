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

## Acknowledgment acks

Acknowledgment is a feature in Kafka that allows the producer to know if the message was successfully delivered to the broker. There are three types of acknowledgment:

- acks=0: The producer does not wait for acknowledgment from the broker.

- acks=1: The producer waits for acknowledgment from the leader broker.

- acks=all: The producer waits for acknowledgment from all in-sync replicas.

# Tips and tricks

## Local Kafka setup

Visit the [Conduktor Getting started page](https://conduktor.io/get-started) and follow the instructions to set up a local Kafka cluster (need Docker).

```bash
curl -L https://releases.conduktor.io/quick-start -o docker-compose.yml && docker compose up -d --wait && echo "Conduktor started on http://localhost:8080"
```

This will start a local Kafka cluster with Conduktor running on [http://localhost:8080](http://localhost:8080).

The bootstrap server is `localhost:19092`.

Thos Kafka Rest Proxy is available at `http://localhost:18082`.

## Download Kafka binaries

Visit the [Apache Kafka downloads page](https://kafka.apache.org/downloads) and download the binaries for your operating system.

> **Note**
> ----
> Choose the binary version.
>

## Kafka commands

### Create a topic

Create a new topic named `my-topic` with 3 partitions.

```bash
kafka-topics.sh --create --topic my-topic --partitions 3 --bootstrap-server localhost:19092
```

### List topics

List all topics in the Kafka cluster.

```bash
kafka-topics.sh --list --bootstrap-server localhost:19092
```

### Describe a topic

Describe the `my-topic` topic.

```bash
kafka-topics.sh --describe --topic my-topic --bootstrap-server localhost:19092
```

### Produce messages

Produce messages to the `my-topic` topic.

```bash
kafka-console-producer.sh --topic my-topic --bootstrap-server localhost:19092
> Hello, Kafka!
```

### Consume messages

Consume messages from the `my-topic` topic.

```bash
kafka-console-consumer.sh --topic my-topic --bootstrap-server localhost:19092
```