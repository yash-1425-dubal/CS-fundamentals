# Chapter 8: Replication

## Introduction

Replication is the process of maintaining multiple copies of data or services across different nodes in a distributed system. This chapter covers various replication strategies, their characteristics, advantages, disadvantages, and use cases.

## Why Do We Need Replication?

Replication is needed because:

1. **Fault tolerance**: Continuing operation despite node failures
2. **Availability**: Ensuring services remain accessible
3. **Performance**: Improving read performance through parallel access
4. **Scalability**: Distributing load across multiple replicas
5. **Geographic distribution**: Placing data closer to users
6. **Disaster recovery**: Protecting against site-wide failures
7. **Load balancing**: Distributing workload evenly
8. **Maintenance**: Enabling rolling upgrades and maintenance

## Core Concepts

### Replica Types

- **Primary/Leader replica**: Processes write operations and coordinates updates
- **Secondary/Follower replica**: Receives updates from primary and serves read requests
- **Peer replica**: All replicas can process both reads and writes
- **Warm standby**: Replica that receives updates but doesn't serve requests
- **Hot standby**: Replica that receives updates and can serve requests
- **Read replica**: Replica optimized for read-only operations

### Replication Methods

- **Synchronous replication**: Writer waits for all replicas to confirm
- **Asynchronous replication**: Writer proceeds immediately after local update
- **Semi-synchronous replication**: Writer waits for subset of replicas to confirm
- **Eager replication**: Updates propagated immediately
- **Lazy replication**: Updates propagated after delay or in batch
- **Active replication**: All replicas process each request
- **Passive replication**: Only primary processes requests, others replicate state

### Consistency Models in Replication

- **Strong consistency**: All replicas see same data at same time
- **Weak consistency**: Replicas may temporarily diverge
- **Eventual consistency**: Replicas will converge if no new updates
- **Monotonic reads**: Successive reads return same or newer values
- **Read-your-writes**: Own writes are always visible
- **Writes-follow-reads**: Writes happen after seen reads

### Replication Protocols

- **Primary-backup**: Primary processes requests, backups replicate state
- **Multi-primary**: Multiple nodes can process write requests
- **Quorum-based**: Read/write operations require agreement from quorum
- **Epidemic/Gossip**: Updates spread through random peer communication
- **State transfer**: Transfer entire state or state differences
- **Operation-based**: Replicate operations rather than state

## How It Works

Replication works by:

1. **Update generation**: Creating updates at the source
2. **Update propagation**: Sending updates to replicas
3. **Update application**: Applying updates at replicas
4. **Consistency maintenance**: Ensuring replicas converge
5. **Failure handling**: Dealing with replica failures and network partitions
6. **Recovery**: Bringing failed replicas back up-to-date
7. **Load distribution**: Spreading requests across replicas

## Architecture

Different architectural approaches to replication:

### Master-Slave (Primary-Secondary) Architecture

- Single master handles all writes
- Slaves replicate from master and handle reads
- Simple to understand and implement
- Single point of failure (master)
- Examples: Traditional MySQL replication, Redis replication

### Multi-Master Architecture

- Multiple nodes can accept write operations
- Requires conflict detection and resolution
- Higher availability and write scalability
- More complex due to conflict handling
- Examples: Cassandra multi-datacenter, Galera Cluster

### Quorum-Based Architecture

- Read and write operations require agreement from quorum
- Can tune consistency vs. availability via quorum sizes
- Examples: Dynamo-style systems, Cassandra

### Peer-to-Peer Architecture

- All nodes are equal and can participate in replication
- Often uses gossip protocols for update dissemination
- Highly decentralized and fault-tolerant
- Examples: IPFS, BitTorrent, blockchain networks

### Hierarchical Architecture

- Replication organized in a hierarchy (e.g., datacenter -> rack -> node)
- Reduces cross-datacenter traffic
- Examples: Content delivery networks, distributed DNS

## Algorithms

### Primary-Backup Replication Algorithm

1. **Normal operation**:
   - Client sends write request to primary
   - Primary executes update locally
   - Primary propagates update to all backups
   - Primary waits for acknowledgments (based on sync mode)
   - Primary returns response to client

2. **Backup operation**:
   - Backup receives update from primary
   - Backup applies update to its state
   - Backup sends acknowledgment to primary

3. **Failover**:
   - Detect primary failure (timeouts, heartbeats)
   - Select new primary from backups
   - Clients redirect to new primary
   - New primary may need to reconcile state

### Quorum-Based Replication Algorithm

1. **Write operation**:
   - Client sends write to W replicas
   - Each replica writes locally and acknowledges
   - Client waits for W acknowledgments
   - Write considered successful when W acks received

2. **Read operation**:
   - Client sends read to R replicas
   - Each replica returns its value and version/timestamp
   - Client waits for R responses
   - Client selects value with highest version/timestamp
   - Read returns selected value

3. **Consistency guarantee**:
   - If R + W > N, then read and write quorums overlap
   - Overlapping quorum ensures reader sees latest write

### Gossip-Based Replication Algorithm

1. **Update generation**:
   - Node generates update locally
   - Node stores update with version/timestamp

2. **Gossip dissemination**:
   - Periodically select random peer
   - Exchange updates with peer
   - Apply any missing updates from peer
   - Send missing updates to peer

3. **Anti-entropy**:
   - Periodically synchronize with random peers
   - Identify and reconcile differences
   - Use Merkle trees or similar for efficient comparison

### Chain Replication Algorithm

1. **Chain setup**:
   - Nodes arranged in a chain: head -> middle -> tail
   - Head processes writes, tail processes reads
   - Intermediate nodes forward updates

2. **Write processing**:
   - Client sends write to head
   - Head updates state and forwards to next node
   - Each node updates and forwards until tail
   - Tail acknowledges back to head
   - Head acknowledges to client

3. **Read processing**:
   - Client sends read to tail
   - Tail returns current state
   - No forwarding needed for reads

4. **Reconfiguration**:
   - Handle node failures by bypassing or replacing
   - Maintain chain invariant during changes

## Example

### Example: Primary-Backup Replication with Synchronous Writes

Consider a system with primary P and backups B1, B2:

1. **Normal write operation**:
   - Client sends write "X=5" to primary P
   - P executes "X=5" locally (X now 5)
   - P sends "X=5" to B1 and B2
   - B1 executes "X=5" locally and sends ack to P
   - B2 executes "X=5" locally and sends ack to P
   - P receives acks from B1 and B2
   - P returns success to client

2. **Concurrent write operation**:
   - Client1 sends write "X=5" to P
   - Client2 sends write "X=7" to P (before Client1 completes)
   - P executes "X=5" locally (X now 5)
   - P sends "X=5" to B1 and B2
   - Before receiving acks, P processes Client2's write
   - P executes "X=7" locally (X now 7, overwriting 5)
   - P sends "X=7" to B1 and B2
   - B1 executes "X=7" locally (X now 7) and sends ack
   - B2 executes "X=7" locally (X now 7) and sends ack
   - P receives acks for both writes
   - P returns success to both clients

3. **Backup failure**:
   - B1 fails and stops responding
   - Client sends write "X=9" to P
   - P executes "X=9" locally (X now 9)
   - P sends "X=9" to B1 (failed) and B2
   - B2 executes "X=9" locally and sends ack
   - Depending on sync mode:
     - Synchronous: P waits for all acks -> blocks indefinitely
     - Async: P returns success after local update
     - Semi-sync: P waits for subset (e.g., 1 of 2) -> returns success after B2 ack

### How It Works

In primary-backup replication:
- Primary serializes all write operations
- Updates are propagated to backups
- Backups apply updates in same order as primary
- Read operations can be served by any replica (may be stale)
- Failover involves selecting a new primary and potentially reconciling state

## Advantages

1. **Fault tolerance**: System continues if replica fails
2. **Improved read performance**: Parallel read access to replicas
3. **Availability**: Service remains accessible during failures
4. **Scalability**: Read load can be distributed across replicas
5. **Geographic distribution**: Replicas can be placed closer to users
6. **Disaster recovery**: Protection against site-wide failures
7. **Load balancing**: Workload can be spread across replicas
8. **Maintenance**: Rolling upgrades possible without downtime

## Disadvantages

1. **Write performance overhead**: Updates must propagate to all replicas
2. **Consistency complexity**: Keeping replicas consistent is challenging
3. **Storage overhead**: Multiple copies consume more storage
4. **Network bandwidth**: Replication consumes network resources
5. **Increased complexity**: More complex to design, implement, and manage
6. **Failure detection**: Detecting replica failures reliably is difficult
7. **Recovery complexity**: Bringing failed replicas up-to-date can be complex
8. **Split brain risk**: Network partitions can cause divergent replicas

## Limitations

1. **Write bottleneck**: Single primary can limit write throughput
2. **Replication lag**: Asynchronous replication causes stale reads
3. **Conflict resolution**: Multi-master requires conflict handling
4. **Geographic latency**: Distance affects replication timing
5. **Bandwidth consumption**: Replication uses network resources
6. **Storage costs**: Multiple replicas increase storage requirements
7. **Consistency guarantees**: Hard to provide strong consistency globally
8. **Reconfiguration complexity**: Adding/removing replicas is complex

## Failure Cases

1. **Replica failure**: Replica crashes or becomes unresponsive
2. **Network partition**: Replicas become isolated from each other
3. **Update loss**: Updates fail to propagate to some replicas
4. **Update duplication**: Updates applied multiple times
5. **Update reordering**: Updates applied in different orders
6. **Inconsistent state**: Replicas diverge due to failed updates
7. **Split brain**: Multiple nodes believe they are primary
8. **Replication lag**: Secondary falls significantly behind primary
9. **Corrupted replica**: Replica state becomes corrupted
10. **Byzantine failure**: Replica behaves arbitrarily or maliciously

## Trade-offs

1. **Sync vs. Async**: Consistency vs. performance
2. **Primary vs. Multi-primary**: Simplicity vs. write scalability
3. **Strong vs. Weak consistency**: Correctness vs. performance/availability
4. **Synchronous vs. Semi-sync**: Guarantee vs. availability
5. **Active vs. Passive**: Fault tolerance vs. performance
6. **Eager vs. Lazy**: Timeliness vs. batching benefits
7. **Centralized vs. Decentralized**: Control vs. fault tolerance
8. **Homogeneous vs. Heterogeneous**: Simplicity vs. flexibility

## Real World Usage

1. **Relational databases**:
   - MySQL: Master-slave replication, Group Replication (multi-master)
   - PostgreSQL: Streaming replication, logical replication
   - Oracle: Data Guard, GoldenGate
   - SQL Server: AlwaysOn Availability Groups, transactional replication

2. **NoSQL databases**:
   - Cassandra: Peer-to-peer gossip-based replication
   - MongoDB: Replica sets with primary-secondary
   - Redis: Master-slave, Redis Cluster (sharding + replication)
   - DynamoDB: Multi-master with conflict resolution
   - Riak: Peer-to-peer with vector clocks and CRDTs

3. **Distributed file systems**:
   - HDFS: Block replication across DataNodes
   - Ceph: Object replication via CRUSH algorithm
   - GlusterFS: Brick replication
   - MooseFS: Chunk replication across servers

4. **Web services and applications**:
   - Load balancers with sticky sessions
   - Database read replicas for scaling reads
   - Microservices with multiple instances
   - Content delivery networks with edge replication

5. **Messaging systems**:
   - RabbitMQ: Queue mirroring across nodes
   - Apache Kafka: Replica factor for topic partitions
   - AWS SQS: Redundancy across availability zones
   - Apache Pulsar: BookKeeper for message storage replication

6. **Blockchain and distributed ledgers**:
   - Bitcoin: Full node replication of blockchain
   - Ethereum: Full node replication with state trie
   - Hyperledger Fabric: Peer nodes with ledger replication
   - Corda: Notary services and ledger replication

7. **Cloud platforms**:
   - AWS: RDS read replicas, DynamoDB global tables
   - Azure: SQL Database geo-replication, Cosmos DB multi-master
   - Google Cloud: Cloud SQL read replicas, Spanner global distribution
   - MongoDB Atlas: Global clusters with regional replicas

8. **DNS and naming systems**:
   - Root DNS servers: Anycast replication
   - TLD servers: Multiple replicas per TLD
   - Authoritative DNS: Master-slave replication
   - Recursive DNS: Cache replication across resolvers

## Interview Perspective

### Common Interview Questions

1. What are the different types of replication and when would you use each?
2. What is the difference between synchronous and asynchronous replication?
3. How does primary-backup replication work?
4. How does multi-master replication handle conflicts?
5. What is quorum-based replication and how does it provide consistency guarantees?
6. How does gossip-based replication work?
7. What are the advantages and disadvantages of replication?
8. How do you handle replica failure and recovery?
9. What is replication lag and how do you monitor it?
10. How do you choose the right replication strategy for an application?

### Common Misconceptions

1. Replication always improves performance for all operations
2. More replicas always mean better fault tolerance
3. Synchronous replication eliminates all consistency concerns
4. Asynchronous replication means data is always inconsistent
5. Multi-master replication is always better than master-slave
6. Replication solves all availability problems
7. All replicas must be identical in hardware and software
8. Replication is only relevant for databases

## Summary

Replication is a fundamental technique in distributed systems for achieving fault tolerance, availability, and performance. Different replication strategies offer various trade-offs between consistency, availability, performance, and complexity. Primary-backup replication provides simplicity but can create write bottlenecks, while multi-master and quorum-based approaches offer better write scalability at the cost of increased complexity. Understanding the characteristics, advantages, disadvantages, and failure modes of different replication approaches is crucial for designing distributed systems that meet specific requirements. Real-world systems often combine multiple replication strategies, using different approaches for different types of data or workloads.