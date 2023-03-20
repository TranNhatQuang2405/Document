<img src="https://stackjava.com/wp-content/uploads/2018/07/mongodb-1.png">

# **`MongoDB`**
## `I> Overall`
### `1.1. NoSQL`
NoSQL databases are purpose built for specific data models and have flexible schemas for building modern applications. NoSQL databases are widely recognized for their ease of development, functionality, and performance at scale. This page includes resources to help you better understand NoSQL databases and to get started.

### `1.2. Introduction of MongoDB`
MongoDB is a document-oriented NoSQL database used for high volume data storage. Instead of using tables and rows as in the traditional relational databases, MongoDB makes use of collections and documents. Documents consist of key-value pairs which are the basic unit of data in MongoDB. Collections contain sets of documents and function which is the equivalent of relational database tables. MongoDB is a database which came into light around the mid-2000s.

### `1.3. Features`
- Ad-hoc queries for optimized, real-time analytics

- Indexing appropriately for better query executions

- Replication for better data availability and stability

- Sharding

- Load balancing

### `1.4. Advantage and Disadvantage`

**`Advantages`**:
- Full cloud-based developer data platform
- Flexible document schemas
- Widely supported and code-native data access
- Change-friendly design
- Powerful querying and analytics
- Easy horizontal scale-out with sharding
- Simple installation
- Cost-effective
- Full technical support and documentation

**`Disadvantages`**:
- Joins not Supported
- Transaction not Supported
- High possibility of data loss
- High Memory Usage
- Limited Data Size
- Limited Nesting

## `II> How to use ?`

### `2.1. Install`
Install Manual: 
- Step 1: Download MongoDB from: https://www.mongodb.com/try/download/community
- Step 2: Install manual by downloaded file
Install In Docker:
- Pull mongoDB image to local
- Create container for mongoDB image

### `2.2. Concepts`

<img src="https://images.viblo.asia/c17118e5-9791-462f-878c-a51778dc357d.jpg">

- `Documents`: The Records in a Document Database. MongoDB stores data as JSON documents. The document data model maps naturally to objects in application code, making it simple for developers to learn and use.

- `Collections`: Grouping Documents. If you are familiar with relational databases, you can think of a collection as a table. But collections in MongoDB are far more flexible. Collections do not enforce a schema, and documents in the same collection can have different fields.

- `Replica Sets`: Ensuring High Availability. When you create a database in MongoDB, the system automatically creates at least two more copies of the data, referred to as a replica set. A replica set is a group of at least three MongoDB instances that continuously replicate data between them, offering redundancy and protection against downtime in the face of a system failure or planned maintenance.

- `Sharding`: Scalability to Handle Massive Data Growth. MongoDB shards data at the collection level, distributing documents in a collection across the shards in a cluster. The result is a scale-out architecture that supports even the largest applications.

- `Indexes`: Indexes support the efficient execution of queries. MongoDB offers a variety of different indexing strategies, including compound indexes on multiple fields. Chosen carefully, indexes speed up queries because queries scan the index instead of reading every document in the collection.

- `Aggregation Pipelines`: MongoDB offers a flexible framework for creating data processing pipelines called aggregation pipelines. It features dozens of stages and over 150 operators and expressions, enabling you to process, transform, and analyze data of any structure at scale
  
- `Programming Languages`: Support almost Programming Languages includes Node.js, C, C++, C#, Go, Java, Perl, PHP, Python, Ruby, Rust, Scala, and Swift. 

### `2.3. Syntax`

| Action          | Code                                                            |
| --------------- | --------------------------------------------------------------- |
| Create database | use test;                                                       |
| Create table    | db.createCollection('students');                                |
| Create record   | db.students.insert({ name:'thanh', gender: 'male'});            |
| Update record   | db.students.update({ _id: 1 },{$set:{ name: 'thanh update' }}); |
| Delete record   | db.students.remove({ _id: 1});                                  |
| Find All record | db.students.find({});                                           |
| Find record     | db.students.find({ name: 'thanh' });                            |

## `III> Replica set`
### `3.1. What is replica set`
- A replica set is a group of mongod instances that maintain the same data set. A replica set contains several data bearing nodes and optionally one arbiter node. Of the data bearing nodes, one and only one member is deemed the primary node, while the other nodes are deemed secondary nodes.

### `3.2. Structure of Replica set`
- The primary node receives all write operations. A replica set can have only one primary capable of confirming writes with { w: "majority" } write concern; although in some circumstances, another mongod instance may transiently believe itself to also be primary. The primary records all changes to its data sets in its operation log, i.e. oplog
  
<img src="https://www.mongodb.com/docs/manual/images/replica-set-read-write-operations-primary.bakedsvg.svg">

- The secondaries replicate the primary's oplog and apply the operations to their data sets such that the secondaries' data sets reflect the primary's data set. If the primary is unavailable, an eligible secondary will hold an election to elect itself the new primary. 

<img src="https://www.mongodb.com/docs/manual/images/replica-set-primary-with-two-secondaries.bakedsvg.svg">



### `3.3. Automatic Failover`

- Vote-based replica set's room projection auto-switching mechanism
- When a primary is inactive, a secondary is elected as the primary of the entire replica set.
- In order to vote successfully, the number of members in a replica set must be odd otherwise two candidates receiving the same number of votes will end up pretending to be both or may lead to a situation where there are two candidates. members all claim to be primary if network partitioning occurs.

<img src="https://images.viblo.asia/full/5330f4eb-1065-46bd-8c2b-aa8d1ed347c4.png">

- In some circumstances (such as you have a primary and a secondary but cost constraints prohibit adding another secondary), you may choose to add a mongod instance to a replica set as an arbiter. An arbiter participates in elections but does not hold data (i.e. does not provide data redundancy).

<img src="https://www.mongodb.com/docs/manual/images/replica-set-primary-with-secondary-and-arbiter.bakedsvg.svg">

## `IV> Sharding`
### `4.1. Overview`
- Sharding is a method for distributing data across multiple machines. MongoDB uses sharding to support deployments with very large data sets and high throughput operations.

- Database systems with large data sets or high throughput applications can challenge the capacity of a single server. For example, high query rates can exhaust the CPU capacity of the server. Working set sizes larger than the system's RAM stress the I/O capacity of disk drives.

- There are two methods for addressing system growth: 
  
**`Vertical Scaling: `** involves increasing the capacity of a single server, such as using a more powerful CPU, adding more RAM, or increasing the amount of storage space. Limitations in available technology may restrict a single machine from being sufficiently powerful for a given workload.

**`Horizontal Scaling: `** involves dividing the system dataset and load over multiple servers, adding additional servers to increase capacity as required. While the overall speed or capacity of a single machine may not be high, each machine handles a subset of the overall workload, potentially providing better efficiency than a single high-speed high-capacity server.

### `4.2. Sharded Cluster`
A MongoDB sharded cluster consists of the following components:

- shard: Each shard contains a subset of the sharded data. Each shard can be deployed as a replica set.

- mongos: The mongos acts as a query router, providing an interface between client applications and the sharded cluster. Starting in MongoDB 4.4, mongos can support hedged reads to minimize latencies.

- config servers: Config servers store metadata and configuration settings for the cluster.

<img src="https://www.mongodb.com/docs/manual/images/sharded-cluster-production-architecture.bakedsvg.svg">

### `4.3. Shard Keys`
- MongoDB uses the shard key to distribute the collection's documents across shards. The shard key consists of a field or multiple fields in the documents.
  
- You select the shard key when sharding a collection.
  
- A document's shard key value determines its distribution across the shards.

### `4.4. Advantages of Sharding`
- Reads / Writes
- Storage Capacity
- High Availability

