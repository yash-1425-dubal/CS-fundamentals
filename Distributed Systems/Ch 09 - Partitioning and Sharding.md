# Chapter 9: Partitioning and Sharding

## Introduction

Partitioning and sharding are techniques for distributing data across multiple nodes in a distributed system to improve scalability, performance, and manageability. This chapter covers various partitioning strategies, their characteristics, advantages, disadvantages, and use cases.

## Why Do We Need Partitioning and Sharding?

Partitioning and sharding are needed because:

1. **Scalability**: Distributing data allows horizontal scaling beyond single node limits
2. **Performance**: Parallel access to different partitions improves throughput
3. **Manageability**: Smaller partitions are easier to backup, restore, and maintain
4. **Availability**: Failure of one partition doesn't affect others
5. **Geographic distribution**: Data can be placed closer to where it's used
6. **Cost efficiency**: Using commodity hardware instead of expensive high-end systems
7. **Resource isolation**: Different workloads can be isolated to different partitions
8. **Hot spot mitigation**: Distributing load prevents overloading specific nodes

## Core Concepts

### Partitioning vs Sharding

- **Partitioning**: General term for dividing data into parts
- **Sharding**: Specific type of partitioning where each part is held on a separate server
- **Horizontal partitioning**: Dividing rows of a table across different partitions
- **Vertical partitioning**: Dividing columns of a table across different partitions
- **Directory-based partitioning**: Using a lookup service to find which partition holds data

### Partitioning Strategies

- **Range partitioning**: Data divided based on value ranges (e.g., A-M, N-Z)
- **Hash partitioning**: Data divided based on hash of key
- **Consistent hashing**: Hash-based partitioning that minimizes reshuffling
- **Dictionary partitioning**: Data divided based on lookup table or directory
- **Composite partitioning**: Combination of multiple partitioning strategies
- **Round-robin partitioning**: Data distributed in cyclic fashion

### Partitioning Keys

- **Primary key partitioning**: Using primary key as partitioning criterion
- **Foreign key partitioning**: Using foreign key to keep related data together
- **Composite key partitioning**: Using multiple columns as partitioning key
- **Hash-based partitioning**: Using hash function on key or columns
- **Random partitioning**: Assigning data randomly to partitions

### Data Distribution

- **Uniform distribution**: Evenly distributing data across partitions
- **Weighted distribution**: Assigning different weights to partitions
- **Dynamic redistribution**: Moving data between partitions as needed
- **Hot partition detection**: Identifying partitions with excessive load
- **Partition rebalancing**: Redistributing load evenly across partitions

### Partition Management

- **Partition creation**: Adding new partitions
- **Partition deletion**: Removing empty or obsolete partitions
- **Partition merging**: Combining small partitions
- **Partition splitting**: Dividing large partitions
- **Partition migration**: Moving data between partitions
- **Partition locking**: Preventing concurrent modifications to partition metadata

## How It Works

Partitioning and sharding work by:

1. **Key extraction**: Extracting partition key from data
2. **Partition determination**: Computing which partition holds the key
3. **Routing**: Directing request to appropriate partition
4. **Data storage**: Storing data in the determined partition
5. **Query processing**: Executing queries against relevant partitions
6. **Result combination**: Combining results from multiple partitions
7. **Maintenance**: Managing partition lifecycle and rebalancing

## Architecture

Different architectural approaches to partitioning:

### Shared-Nothing Architecture

- Each node is independent and self-sufficient
- No shared memory or disk storage
- Nodes communicate only through network
- Examples: Google Spanner, Apache Cassandra, MongoDB sharded clusters

### Shared-Disk Architecture

- Multiple nodes share access to same disk storage
- Each node has its own memory and processors
- Examples: Oracle RAC, Microsoft SQL Server AlwaysOn FCI

### Shared-Memory Architecture

- Multiple nodes share same memory space
- Each node has its own processors
- Rare in distributed systems due to scalability limits
- Examples: Some SMP systems, specialized hardware

### Hybrid Architecture

- Combination of different architectural approaches
- May use shared-nothing for compute, shared-disk for storage
- Examples: Cloud databases with separated compute and storage layers

## Algorithms

### Range Partitioning Algorithm

1. **Define ranges**: Specify value ranges for each partition (e.g., 0-100, 101-200)
2. **Extract key**: Get partitioning key from data
3. **Find range**: Determine which range contains the key
4. **Route to partition**: Send data to partition responsible for that range
5. **Adjust ranges**: Split or merge ranges as needed for load balancing

### Hash Partitioning Algorithm

1. **Select hash function**: Choose hash function (e.g., MD5, SHA-1, MurmurHash)
2. **Extract key**: Get partitioning key from data
3. **Compute hash**: Apply hash function to key
4. **Determine partition**: Map hash value to partition (e.g., hash % num_partitions)
5. **Handle collisions**: Ensure uniform distribution despite hash collisions

### Consistent Hashing Algorithm

1. **Hash space**: Treat hash output as circular space (0 to 2^32-1)
2. **Place nodes**: Hash node identifiers and place them on the circle
3. **Place keys**: Hash keys and place them on the circle
4. **Assign responsibility**: Each node is responsible for keys from itself to next node
5. **Handle node addition**: New node takes over portion from its predecessor
6. **Handle node removal**: Successor takes over responsibility from removed node
7. **Virtual nodes**: Use multiple hash points per physical node for better distribution

### Directory-Based Partitioning Algorithm

1. **Directory service**: Maintain lookup service mapping keys to partitions
2. **Extract key**: Get partitioning key from data
3. **Query directory**: Ask directory service which partition holds key
4. **Route request**: Send data to returned partition
5. **Update directory**: Modify mappings when partitions change
6. **Cache lookups**: Cache directory responses to reduce latency

### Rebalancing Algorithm

1. **Detect imbalance**: Monitor partition loads (size, access frequency)
2. **Plan movement**: Determine which data to move where
3. **Prepare destination**: Ensure target partition ready to receive data
4. **Transfer data**: Copy data from source to destination partitions
5. **Update routing**: Modify partition mappings to reflect new locations
6. **Clean source**: Remove transferred data from source partition
7. **Verify consistency**: Ensure data integrity after transfer

## Example

### Example: User Data Partitioning by Hash

Consider partitioning user data by user ID using hash partitioning:

1. **Setup**:
   - 4 partitions (P0, P1, P2, P3)
   - Hash function: H(key) = key % 4
   - User IDs: 1001, 1002, 1003, 1004, 1005, 1006

2. **Data insertion**:
   - User 1001: H(1001) = 1001 % 4 = 1 → Partition P1
   - User 1002: H(1002) = 1002 % 4 = 2 → Partition P2
   - User 1003: H(1003) = 1003 % 4 = 3 → Partition P3
   - User 1004: H(1004) = 1004 % 4 = 0 → Partition P0
   - User 1005: H(1005) = 1005 % 4 = 1 → Partition P1
   - User 1006: H(1006) = 1006 % 4 = 2 → Partition P2

3. **Query processing**:
   - Get user 1003: H(1003) = 3 → Query Partition P3
   - Get users 1001 and 1005: Both hash to 1 → Query Partition P1
   - Get all users: Query all partitions and combine results

4. **Rebalancing** (adding 5th partition):
   - New hash function: H(key) = key % 5
   - User 1001: H(1001) = 1001 % 5 = 1 → Still P1
   - User 1002: H(1002) = 1002 % 5 = 2 → Still P2
   - User 1003: H(1003) = 1003 % 5 = 3 → Still P3
   - User 1004: H(1004) = 1004 % 5 = 4 → Move to new P4
   - User 1005: H(1005) = 1005 % 5 = 0 → Move to new P0
   - User 1006: H(1006) = 1006 % 5 = 1 → Still P1

### How It Works

In hash partitioning:
- Data is distributed based on hash of partitioning key
- Uniform hash function ensures even distribution
- Adding/removing partitions requires rehashing and data movement
- Consistent hashing minimizes reshuffling when partitions change
- Range partitioning keeps related data together but may cause hot spots

## Advantages

1. **Horizontal scalability**: Scale out by adding more nodes
2. **Improved query performance**: Parallel execution across partitions
3. **Reduced contention**: Different partitions can be accessed concurrently
4. **Fault isolation**: Failure affects only specific partition
5. **Geographic locality**: Place partitions close to users
6. **Cost effectiveness**: Use commodity hardware instead of high-end systems
7. **Manageability**: Smaller partitions easier to backup and maintain
8. **Load balancing**: Distribute workload evenly across nodes

## Disadvantages

1. **Cross-partition transactions**: Transactions spanning partitions are complex
2. **Rebalancing overhead**: Moving data between partitions consumes resources
3. **Partition skew**: Uneven data distribution creates hot spots
4. **Increased complexity**: More complex to design, implement, and manage
5. **Limited partitioning schemes**: Some queries don't align with partitioning
6. **Join complexity**: Joining data across partitions requires special handling
7. **Partition key selection**: Poor key choice leads to uneven distribution
8. **Hot spot mitigation**: Requires ongoing monitoring and intervention

## Limitations

1. **Partitioning key impact**: Performance heavily depends on key selection
2. **Cross-partition queries**: May require querying multiple partitions
3. **Transaction complexity**: ACID transactions across partitions are challenging
4. **Rebalancing disruption**: Data movement affects ongoing operations
5. **Partition explosion**: Too many partitions create management overhead
6. **Skew handling**: Detecting and correcting skew requires sophisticated tools
7. **Partition loyalty**: Some data access patterns benefit from keeping related data together
8. **Schema changes**: Modifying partitioning scheme requires significant effort

## Failure Cases

1. **Partition unavailability**: Partition becomes inaccessible due to node failure
2. **Data loss**: Partition data corrupted or lost
3. **Misrouting**: Requests sent to wrong partition due to hash collision or error
4. **Split brain**: Multiple nodes believe they own same partition
5. **Rebalancing failure**: Data movement incomplete or corrupted
6. **Partition overlap**: Same data stored in multiple partitions
7. **Partition gaps**: No partition responsible for certain key ranges
8. **Metadata corruption**: Partition mapping information becomes corrupted
9. **Hot partition**: Single partition receives disproportionate load
10. **Cascading failures**: Failure in one partition overloads others

## Trade-offs

1. **Range vs. Hash**: Ordered access vs. uniform distribution
2. **Number of partitions**: More partitions vs. management overhead
3. **Static vs. Dynamic**: Fixed partitioning vs. adaptive rebalancing
4. **Uniform vs. Weighted**: Equal distribution vs. workload-aware distribution
5. **Key complexity**: Simple keys vs. composite keys for better distribution
6. **Virtual nodes**: Better distribution vs. increased metadata
7. **Lazy vs. Eager**: Delayed rebalancing vs. immediate consistency
8. **Local vs. Global**: Partition-local vs. cross-partition operations

## Real World Usage

1. **NoSQL databases**:
   - Apache Cassandra: Consistent hashing with virtual nodes
   - MongoDB: Range-based sharding with config servers
   - Amazon DynamoDB: Hash and range partitioning with automatic scaling
   - HBase: Range partitioning based on row keys
   - Redis Cluster: Hash partitioning with 16384 slots

2. **NewSQL databases**:
   - Google Spanner: Hierarchical hash-range partitioning with Paxos groups
   - CockroachDB: Range partitioning with Raft replication per range
   - Vitess: MySQL sharding with consistent hashing
   - TiDB: Range partitioning with Raft replication

3. **Data warehouses and analytics**:
   - Amazon Redshift: Columnar storage with distribution styles
   - Google BigQuery: Automatic partitioning with sliding window
   - Apache Parquet/ORC: Columnar formats with partitioning support
   - Snowflake: Automatic micro-partitioning with clustering

4. **Search and indexing systems**:
   - Elasticsearch: Sharding based on hash of document ID
   - Apache Solr: Hash-based sharding with ZooKeeper coordination
   - Lucene: Index partitioning for parallel search
   - Splunk: Bucket-based indexing with search factor

5. **Messaging and streaming systems**:
   - Apache Kafka: Partitioning based on hash of message key
   - Amazon Kinesis: Sharding based on hash of partition key
   - RabbitMQ: Consistent hashing exchange for queue distribution
   - Apache Pulsar: Segment-based storage with bookkeeper

6. **File systems and storage**:
   - HDFS: Block distribution across DataNodes
   - Ceph: CRUSH algorithm for pseudo-random distribution
   - GlusterFS: Elastic hashing algorithm for data distribution
   - MooseFS: Chunk distribution across servers

7. **Content delivery networks**:
   - Cache partitioning based on URL hash or geographic location
   - Request routing based on client IP or geolocation
   - Content distribution based on popularity and locality
   - Edge computing with workload-specific partitioning

8. **Distributed computing frameworks**:
   - Apache Spark: RDD partitioning based on hash or range
   - Apache Flink: Key-based partitioning for stateful operations
   - MapReduce: Hash partitioning for shuffle phase
   - Dask: Partitioning based on data locality and workload

## Interview Perspective

### Common Interview Questions

1. What is the difference between partitioning and sharding?
2. How does range partitioning work and when is it appropriate?
3. How does hash partitioning work and what are its advantages?
4. What is consistent hashing and how does it improve upon regular hashing?
5. How does directory-based partitioning work?
6. What are the challenges of cross-partition transactions?
7. How do you handle rebalancing in a partitioned system?
8. How do you detect and handle hot partitions?
9. What are the advantages and disadvantages of partitioning?
10. How do you choose the right partitioning strategy for an application?

### Common Misconceptions

1. Partitioning always improves performance for all workloads
2. More partitions always mean better performance
3. Hash partitioning eliminates all hot spots
4. Range partitioning always keeps related data together
5. Partitioning solves all scalability problems
6. Rebalancing is a simple and risk-free operation
7. All data should be partitioned for maximum scalability
8. Partitioning keys should always be based on primary keys

## Summary

Partitioning and sharding are essential techniques for scaling distributed systems beyond the limits of single nodes. Different partitioning strategies offer various trade-offs between performance, complexity, and functionality. Range partitioning provides ordered access but can create hot spots, hash partitioning offers uniform distribution but scatters related data, and consistent hashing minimizes reshuffling when nodes are added or removed. Understanding the characteristics, advantages, disadvantages, and failure modes of different partitioning approaches is crucial for designing distributed systems that can scale effectively while maintaining correctness and performance. Real-world systems often combine multiple partitioning strategies, using different approaches for different types of data or workloads, and implement sophisticated rebalancing mechanisms to handle changing load patterns.