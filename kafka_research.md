<img src="https://topdev.vn/blog/wp-content/uploads/2019/05/kafka.png">

# `Apache Kafka`
## `I> Overall`
### `1.1. Introduction`
Kafka is a distributed system consisting of servers and clients that communicate via a high-performance TCP network protocol. It can be deployed on bare-metal hardware, virtual machines, and containers in on-premise as well as cloud environments.

`Servers`: Kafka is run as a cluster of one or more servers that can span multiple datacenters or cloud regions. Some of these servers form the storage layer, called the brokers. Other servers run Kafka Connect to continuously import and export data as event streams to integrate Kafka with your existing systems such as relational databases as well as other Kafka clusters. To let you implement mission-critical use cases, a Kafka cluster is highly scalable and fault-tolerant: if any of its servers fails, the other servers will take over their work to ensure continuous operations without any data loss.

`Clients`: They allow you to write distributed applications and microservices that read, write, and process streams of events in parallel, at scale, and in a fault-tolerant manner even in the case of network problems or machine failures. Kafka ships with some such clients included, which are augmented by dozens of clients provided by the Kafka community: clients are available for Java and Scala including the higher-level Kafka Streams library, for Go, Python, C/C++, and many other programming languages as well as REST APIs.

### `1.2. Architecture`

General Architecture of Apache Kafka:

<img src="https://topdev.vn/blog/wp-content/uploads/2019/05/kafka-simple.png">

Architecture details of Apache Kafka:

<img src="https://topdev.vn/blog/wp-content/uploads/2019/05/kafka-structure.png">

### `1.3. Concepts`
| Concept             | Description                                                                           |
| ------------------- | ------------------------------------------------------------------------------------- |
| TOPIC | Data transfer in Kafka by topic, when you need to pass data to different applications, it will create different topics. |
| PRODUCER  | Kafka stores and categorizes messages by topic, uses a producer to publish messages to topics. The data is sent to the topic's partition stored on the Broker.|
| CONSUMER | Kafka uses consumers to subscribe to topics, consumers are identified by group names. Multiple consumers can read the same topic.|
| CLUSTER | Kafka Cluster is a set of servers, each set in the Cluster is called a Broker |
| BROKER | Broker is a Kafka Server, acting as a bridge between Message Pulisher and Message Consumer so that these two components can exchange Messages with each other. |
| PARTITION | This is where the data for a topic is stored. A topic can have one or more partitions. On each partition, the data is stored permanently and is assigned an ID called offset. In a Kafka cluster, a partition can be replicated to many copies. There is a leader responsible for reading and writing data and the rest are called followers. When the leader version is faulty, there will be a follower version to be the replacement leader. If you want to use multiple consumers to read the data of a topic in parallel, that topic needs to have multiple partitions.|
| ZOOKEEPER | used to manage and arrange brokers.| 


### `1.3. Kafka APIs`

In addition to command line tooling for management and administration tasks, Kafka has five core APIs for Java and Scala:

- The Admin API to manage and inspect topics, brokers, and other Kafka objects.
- The Producer API to publish (write) a stream of events to one or more Kafka topics.
- The Consumer API to subscribe to (read) one or more topics and to process the stream of events produced to them.
- The Kafka Streams API to implement stream processing applications and microservices. It provides higher-level functions to process event streams, including transformations, stateful operations like aggregations and joins, windowing, processing based on event-time, and more. Input is read from one or more topics in order to generate output to one or more topics, effectively transforming the input streams to output streams.
- The Kafka Connect API to build and run reusable data import/export connectors that consume (read) or produce (write) streams of events from and to external systems and applications so they can integrate with Kafka. For example, a connector to a relational database like PostgreSQL might capture every change to a set of tables. However, in practice, you typically don't need to implement your own connectors because the Kafka community already provides hundreds of ready-to-use connectors.

### `1.4 Main Features`
- Using Kafka to deliver messages
- Event Streaming Kafka
- Storing data on the Kafka system

### `1.5. Advantage and Disadvantage`

**`Advantage:`**

- Open source
- High Throughput: Capable of processing large amounts of information in a - continuous manner, with almost no waiting time
- High frequency: Can handle many messages and many types of topics at the same time
- Scalability: Easily expand as needed
- Automatically archive messages, easy to check back
Large user community, quick support when needed

**`Disadvantage:`**

- There is no complete set of monitoring tools: There are many different tools, but each tool only meets a certain management feature, such as: Kafka tool (offset manager) GUI tool - managing topics and consumers, Lense - support query message, Akhq - Kafka management toolbox and view data inside Kafka
- Can't select topic by wildcard: User will need to use exact topic name to process message
- Reduced performance: Increasing message size causes consumers and producers to compress and decompress messages, thereby slowing down memory, affecting throughput and performance.
- Slow processing: Sometimes the number of queues in Kafka cluster spikes causing Kafka to process slower.

## `II> How to set up`