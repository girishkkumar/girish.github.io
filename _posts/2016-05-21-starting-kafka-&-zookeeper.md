---
layout: post
title: "Starting Zookeeper & Kafka"
date: 2016-05-21
---

**_Starting zookeeper:_**

```
/Apache/zookeeper/zookeeper-3.4.8/bin$ ./zkServer.sh start ../conf/zoo1.cfg

/Apache/zookeeper/zookeeper-3.4.8/bin$ ./zkServer.sh start ../conf/zoo2.cfg

/Apache/zookeeper/zookeeper-3.4.8/bin$ ./zkServer.sh start ../conf/zoo3.cfg

```
Run the jps command to know the instances running or not

```
/Apache/zookeeper/zookeeper-3.4.8/bin$ jps
```

To know whether the instance is leader or follower run the below command for all the instances

```
/Apache/zookeeper/zookeeper-3.4.8/bin$ zkServer.sh status ../conf/zoo1.cfg

/Apache/zookeeper/zookeeper-3.4.8/bin$ zkServer.sh status ../conf/zoo2.cfg

/Apache/zookeeper/zookeeper-3.4.8/bin$ zkServer.sh status ../conf/zoo3.cfg
```

Once all the server instances are started, run the client command below:

```
/Apache/zookeeper/zookeeper-3.4.8/bin$ zkCli.sh -server localhost:2181,localhost:2182,localhost:2183
```

to create a zookeeper node

```
create /zookeeper2 testdata
```

to see the list of znodes

```
ls /
```

to see the znode data of a node

```
get /zookeeper2
```

to update a specific 

```
set /zookeeper2 testdataupdated
```

to delete the node

```
delete /zookeeper2
```

**_Starting kafka:_**

Apache Kafka Quickstart Documentation

```
http://kafka.apache.org/documentation.html#quickstart
```

```
/Apache/Kafka/kafka_2.11-0.9.0.1/bin$ ./kafka-server-start.sh ../config/server.properties
```

Once kafka gets started, we need to create the topic to post data to it

```
/Apache/Kafka/kafka_2.11-0.9.0.1/bin$ ./kafka-topics.sh --create --zookeeper localhost:2181 
--replication-factor 1 --partitions 1 --topic girishTopic

Created topic "girishTopic".
```

To see list of created topics

```
/Apache/Kafka/kafka_2.11-0.9.0.1/bin$ ./kafka-topics.sh --list --zookeeper localhost:2181

girishTopic
```

Start the console producer and consumer 

```
/Apache/Kafka/kafka_2.11-0.9.0.1/bin$ ./kafka-console-producer.sh --topic girishTopic 
--broker-list localhost:9092
```

```
/Apache/Kafka/kafka_2.11-0.9.0.1/bin$ ./kafka-console-consumer.sh --topic girishTopic 
--zookeeper localhost:2181 --from-beginning
```
When both producer and consumer are started, post something on the producer, the data should be visible on the consumer.

Stopping the kafka server:

```
/Apache/Kafka/kafka_2.11-0.9.0.1/bin$ ./kafka-server-stop.sh ../config/server.properties
```
