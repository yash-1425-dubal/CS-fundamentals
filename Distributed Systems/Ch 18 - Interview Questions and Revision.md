# Chapter 18: Interview Questions and Revision

## Introduction

This chapter consolidates key concepts from all previous chapters into a format suitable for interview preparation and revision. It includes common interview questions, key points to remember, and revision strategies.

## Why Do We Need Interview Questions and Revision?

Interview questions and revision are needed because:

1. **Interview preparation**: Helps candidates prepare for technical interviews
2. **Knowledge consolidation**: Brings together concepts from all chapters
3. **Identifying gaps**: Highlights areas that need further study
4. **Practice application**: Applies theoretical knowledge to practical scenarios
5. **Confidence building**: Builds confidence through preparation and practice
6. **Time efficiency**: Focuses revision on most important concepts
7. **Pattern recognition**: Helps recognize common question patterns
8. **Performance improvement**: Improves ability to answer under pressure

## Core Concepts

### Key Points from Each Chapter

**Chapter 1: Introduction and Fundamentals**
- Definition: Collection of independent computers appearing as single coherent system
- Goals: Transparency, openness, scalability, fault tolerance, concurrency, security
- Characteristics: Autonomy, concurrency, scalability, fault tolerance, transparency, heterogeneity
- Advantages: Resource sharing, scalability, fault tolerance, performance, availability, cost-effectiveness
- Disadvantages: Complexity, communication overhead, security challenges, data consistency, debugging difficulty, network dependency

**Chapter 2: System Models and Architecture**
- Architectural models: Centralized, decentralized, hierarchical, peer-to-peer, client-server
- Interaction models: Shared memory, message passing, RPC, distributed shared memory, event-based
- Failure models: Crash-stop, crash-recovery, omission, timing, Byzantine
- Security models: Threat, protection, trust, authentication, authorization

**Chapter 3: Communication and Remote Procedure Calls**
- Message passing: Synchronous/asynchronous, blocking/non-blocking, reliable/unreliable
- Request-response: Client sends request, server processes, client receives response
- RPC: Transparent remote procedure call with stub generation and marshalling
- RMI: Object-oriented remote method invocation
- REST: Resource-based, stateless, cacheable, uniform interface
- gRPC: Protocol Buffers + HTTP/2 with streaming support
- Serialization: Text-based (JSON, XML) vs binary-based (Protocol Buffers, Avro)
- Message queues: Point-to-point and publish-subscribe patterns
- Service discovery: Finding services in dynamic environments
- API gateways: Single entry point with routing, composition, translation, security
- Backpressure: Feedback mechanism when receiver overwhelmed

**Chapter 4: Time Clocks and Ordering**
- Physical clocks: Hardware-based with drift, skew, resolution, accuracy, precision
- Clock synchronization: Cristian's algorithm, Berkeley algorithm, NTP, PTP
- Logical clocks: Lamport timestamps, vector clocks, version vectors
- Happens-before: Causal relationship defining event ordering
- Ordering types: Causal, total, partial ordering
- Algorithms: Cristian's, Berkeley, NTP, Lamport timestamps, vector clocks

**Chapter 5: Logical Clocks and Vector Clocks**
- Lamport timestamps: Monotonic counters with message passing
- Vector clocks: Vector of counters (one per process) for precise causality
- Version vectors: Specialized for conflict detection in replicated data
- Matrix clocks: Generalization of vector clocks
- Interval tree clocks: Efficient alternative to vector clocks
- Dotted version vectors: Combine version vectors with dotted attributes
- Algorithms: Lamport timestamp, vector clock, version vector algorithms

**Chapter 6: Distributed State and Snapshots**
- Global state vs local state: Combined vs individual node state
- Consistent global state: State that could have occurred in some execution
- Marker messages: Special messages delineating snapshot boundaries
- Chandy-Lamport algorithm: Fundamental snapshot algorithm using markers
- Snapshot use cases: Deadlock detection, termination detection, garbage collection, checkpointing
- Algorithms: Chandy-Lamport snapshot, Dijkstra-Scholten termination detection

**Chapter 7: Consistency Models**
- Consistency spectrum: Strict → linearizability → sequential → causal → eventual → weak
- Key properties: Ordering guarantees, visibility, synchronization, performance, fault tolerance
- Models: Strict consistency, linearizability, sequential consistency, causal consistency, eventual consistency, weak consistency
- Algorithms: Linearizability verification, sequential consistency checking, vector clock causality, quorum calculation
- Implementations: Primary-backup, quorum-based, state machine, lazy replication, CRDTs

**Chapter 8: Replication**
- Replica types: Primary/leader, secondary/follower, peer, warm standby, hot standby, read replica
- Replication methods: Synchronous, asynchronous, semi-synchronous, eager, lazy, active, passive
- Consistency models: Strong, weak, eventual, monotonic reads, read-your-writes, writes-follow-reads
- Protocols: Primary-backup, multi-primary, quorum-based, epidemic/gossip, state transfer, operation-based
- Algorithms: Primary-backup, quorum-based, gossip-based, chain replication

**Chapter 9: Partitioning and Sharding**
- Partitioning vs sharding: General term vs specific horizontal partitioning
- Strategies: Range, hash, consistent hashing, directory-based, composite, round-robin
- Keys: Primary key, foreign key, composite key, hash-based, random
- Data distribution: Uniform, weighted, dynamic redistribution, hot partition detection
- Partition management: Creation, deletion, merging, splitting, migration, locking
- Algorithms: Range partitioning, hash partitioning, consistent hashing, directory-based, rebalancing

**Chapter 10: Distributed Transactions**
- ACID properties: Atomicity, consistency, isolation, durability
- Transaction models: Flat, nested, distributed, workflow, saga
- Protocols: Two-phase commit (2PC), three-phase commit (3PC), Paxos Commit, Raft Commit, Saga
- Participants: Coordinator/transaction manager, participants/resource managers, transaction branches
- States: Active, partially committed, committed, aborted, in-doubt
- Algorithms: 2PC (prepare/commit phases), 3PC (canCommit/preCommit/doCommit), Paxos Commit, Saga

**Chapter 11: Consensus and Coordination**
- Consensus problem: Agreement, validity, termination, integrity
- Properties: Safety (agreement, validity), liveness (termination), fault tolerance, performance
- Leader election: Choosing special node to coordinate activities
- Coordination mechanisms: Distributed locks, barriers, queues, watchers/notifications, sequencers
- Quorum systems: Subsets whose intersection guarantees consistency
- Algorithms: Paxos (prepare/promise, accept/accepted, learn), Raft (leader election, log replication, safety), Viewstamped Replication, BFT algorithms (PBFT), Chandra-Toueg

**Chapter 12: Fault Tolerance and Failure Detection**
- Failure models: Crash-stop, crash-recovery, omission, timing, Byzantine, performance
- Fault tolerance techniques: Replication, redundancy, diversity, isolation, degradation, recovery, masking
- Failure detection: Heartbeats, timeouts, monitoring, gossip, phi accrual, threshold-based
- Reliability metrics: MTBF, MTTR, availability, reliability, FIT
- Algorithms: Heartbeat-based, phi accrual, gossip-based, threshold-based

**Chapter 13: Distributed Storage Systems**
- Storage models: Block, file, object, table, graph
- Consistency models: Strong, eventual, session, read-your-writes, monotonic reads, prefix reads
- Architectures: Shared-nothing, shared-disk, shared-memory, hybrid
- Data distribution: Replication, partitioning/sharding, erasure coding, hierarchical storage
- Access patterns: Sequential, random, streaming, batch, real-time
- Algorithms: Consistent hashing, erasure coding, DHT (Chord), LSM-Tree, quorum-based replication

**Chapter 14: Distributed Caching and Messaging**
- Distributed caching: Temporary storage for faster retrieval
- Caching strategies: Cache-aside, write-through, write-back, read-through, refresh-ahead, partitioning
- Cache eviction: LRU, LFU, FIFO, random, LRU-K, ARC
- Messaging patterns: Point-to-point, publish-subscribe, request-reply, pipeline, fan-out/fan-in
- Message brokers: Queues, topics, exchanges, bindings, routing keys, dead letter queues
- Streaming concepts: Stream, event, window, event time, processing time, watermark
- Algorithms: LRU cache, LFU cache, consistent hashing for caching, AMQP routing, stream processing windows

**Chapter 15: Scalability and Load Balancing**
- Types of scalability: Vertical, horizontal, diagonal, elastic, geographic
- Load balancing: Distribution of network traffic across multiple servers
- Load balancer: Device/software distributing traffic
- Algorithms: Round-robin, least connections, IP hash, weighted response time, resource-based, consistent hashing
- Metrics: Throughput, latency, concurrent users, response time, error rate, resource utilization
- Bottlenecks: CPU, memory, I/O, network, software

**Chapter 16: CAP PACELC and Trade-offs**
- CAP theorem: Can only guarantee two of Consistency, Availability, Partition tolerance
- PACELC theorem: If Partition then (A vs C) else (Latency vs Consistency)
- Consistency models: Strong, weak, tunable
- Availability measures: Uptime percentage, MTBF, MTTR, error rate, request success rate
- Latency metrics: Response time, throughput, percentile latency, tail latency
- Architectures: CA, CP, AP, EL, EC systems
- Algorithms: Consistency level selection, availability optimization, latency reduction

**Chapter 17: Real World Distributed Systems**
- Google systems: GFS, MapReduce, Bigtable, Spanner, Borg/Omega, Pub/Sub, Chubby, Dapper, BigQuery
- Amazon Dynamo-style: DynamoDB, Cassandra, Riak, Voldemort
- Netflix: Open Connect, microservices, Chaos Monkey, Titus, Zuul, Eureka, Hystrix, Ribbon, Archaius, Atlas
- Apache Kafka: Publish-subscribe, partitioning, replication, consumer groups, stream processing, Connect API
- Cassandra: Peer-to-peer, consistent hashing, tunable consistency, write-optimized, eventual consistency, linear scalability, flexible schema, CQL, compaction
- Redis: In-memory, persistence options, data structures, replication, clustering, pub/sub, Lua scripting, LRU/LFU eviction, transactions, high performance
- ZooKeeper: Hierarchical namespace, strong consistency, high availability, primitives, watch mechanism, FIFO ordering, atomic messaging, failure detection, simple API
- etcd: Raft consensus, MVCC storage, watch capabilities, lease mechanism, alarm system, backup/restore, authentication, gRPC API, HTTP/JSON gateway, metrics
- Hadoop ecosystem: HDFS, MapReduce, YARN, Hive, Pig, HBase, Spark, Kafka, Flume, Sqoop, Oozie
- CDNs: Edge servers, caching, request routing, origin fetch, cache invalidation, SSL/TLS termination, DDoS protection, real-time analytics, dynamic content, video streaming

## Common Interview Questions

### Fundamentals and Concepts

1. What is a distributed system and what are its main goals?
2. Explain the difference between horizontal and vertical scaling.
3. What is transparency in distributed systems and what are its types?
4. Describe the advantages and disadvantages of distributed systems.
5. What are the main characteristics of distributed systems?
6. Explain the client-server and peer-to-peer architectural models.
7. What are the different failure models in distributed systems?
8. Describe the CAP theorem and its implications.
9. What is the PACELC theorem and how does it extend CAP?
10. Explain the difference between strong and eventual consistency.

### Communication and RPC

11. How does RPC work and what are its main components?
12. What is the difference between synchronous and asynchronous communication?
13. Explain the request-response communication pattern.
14. What is REST and what are its constraints?
15. How does gRPC differ from traditional RPC?
16. What is serialization and why is it important in distributed systems?
17. Explain the publish-subscribe messaging pattern.
18. How do message queues work and what are their benefits?
19. What is service discovery and why is it needed?
20. What is an API gateway and what functions does it provide?

### Time and Ordering

21. What is the difference between physical and logical clocks?
22. Explain Lamport timestamps and how they work.
23. What are vector clocks and how do they improve upon Lamport timestamps?
24. What is the happens-before relationship?
25. Explain Cristian's algorithm for clock synchronization.
26. How does the Berkeley algorithm work?
27. What is NTP and how does it achieve clock synchronization?
28. What is the difference between causal, total, and partial ordering?

### Consistency and Replication

29. What is linearizability and how does it differ from sequential consistency?
30. Explain the different consistency models (causal, eventual, weak, etc.).
31. How does primary-backup replication work?
32. What is quorum-based replication and how does it provide consistency guarantees?
33. Explain the difference between synchronous and asynchronous replication.
34. What is the write-ahead log and how is it used in replication?
35. How do you handle conflicts in multi-master replication?
36. What is read repair and when is it used?

### Transactions and Consensus

37. What are the ACID properties and how do they apply to distributed transactions?
38. Explain the two-phase commit (2PC) protocol.
39. What is the blocking problem in 2PC and how does 3PC address it?
40. What is the Paxos consensus algorithm?
41. How does the Raft consensus algorithm work?
42. What is leader election and how is it implemented in consensus algorithms?
43. What is the Saga pattern and when is it used?
44. Explain the difference between committed and aborted transaction states.
45. What is an in-doubt transaction and how is it resolved?

### Fault Tolerance and Storage

46. What are the different fault tolerance techniques used in distributed systems?
47. How does heartbeat-based failure detection work?
48. What is the phi accrual failure detector?
49. Explain the difference between crash-stop and crash-recovery failures.
50. What is erasure coding and how does it compare to replication?
51. Explain the consistent hashing algorithm and its use in distributed systems.
52. What is the difference between object, file, and block storage?
53. How does the LSM-Tree algorithm work?
54. What are the different consistency models in distributed storage?

### Caching, Messaging, and Scalability

55. What is the cache-aside pattern and how does it work?
56. Explain the LRU cache eviction policy.
57. What are the different caching strategies (write-through, write-back, etc.)?
58. How does consistent hashing improve distributed caching?
59. What are the different messaging patterns (point-to-point, pub/sub, etc.)?
60. How do message brokers like RabbitMQ and Apache Kafka differ?
61. What is round-robin load balancing and what are its limitations?
62. How does least connections load balancing work?
63. What is IP hash load balancing and when is it appropriate?
64. Explain the consistent hashing algorithm for load balancing.
65. What are the different types of scalability and when would you use each?

### Real World Systems

66. What are some key lessons learned from Google's distributed systems?
67. How do Dynamo-style systems achieve high availability and scalability?
68. What makes Apache Kafka suitable for real-time stream processing?
69. How does Redis achieve high performance as an in-memory data store?
70. What are the key features of ZooKeeper that make it useful for coordination?
71. How does etcd use Raft to provide strong consistency and high availability?
72. What are the main components of the Hadoop ecosystem and their purposes?
73. How do CDNs improve content delivery performance and reliability?
74. What are some common patterns observed across different real-world distributed systems?
75. How do real-world systems handle the trade-offs described in CAP and PACELC theorems?

## Revision Strategies

### Topic-Based Revision

1. **Fundamentals**: Review Chapters 1-2 for basic concepts and models
2. **Communication**: Review Chapters 3-4 for messaging and timing
3. **Consistency**: Review Chapters 5-7 for logical clocks and consistency models
4. **Replication and Partitioning**: Review Chapters 8-9 for data distribution
5. **Transactions and Consensus**: Review Chapters 10-11 for coordination mechanisms
6. **Fault Tolerance**: Review Chapter 12 for failure handling
7. **Storage Systems**: Review Chapter 13 for data storage
8. **Performance Optimization**: Review Chapters 14-15 for caching, messaging, and scaling
9. **Trade-offs**: Review Chapter 16 for CAP PACELC and design decisions
10. **Real World Applications**: Review Chapter 17 for practical implementations

### Question-Based Revision

1. **Definition questions**: Focus on "what is" and "define" questions
2. **Explanation questions**: Focus on "how does" and "explain" questions
3. **Comparison questions**: Focus on "difference between" and "compare" questions
4. **Application questions**: Focus on "when would you use" and "scenario" questions
5. **Algorithm questions**: Focus on "how does this algorithm work" questions
6. **Trade-off questions**: Focus on "advantages and disadvantages" questions
7. **Real-world questions**: Focus on "examples of" and "real-world systems" questions

### Active Recall Techniques

1. **Flashcards**: Create flashcards for key terms, definitions, and algorithms
2. **Diagram drawing**: Practice drawing diagrams from memory (architecture, algorithms, data flows)
3. **Teaching others**: Explain concepts to others to reinforce understanding
4. **Problem solving**: Work through hypothetical scenarios and design problems
5. **Summary writing**: Write one-paragraph summaries of each chapter from memory
6. **Question generation**: Create your own interview questions for each topic

### Common Mistakes to Avoid

1. **Confusing similar concepts**: e.g., Lamport timestamps vs vector clocks
2. **Overlooking assumptions**: Remembering the conditions under which algorithms work
3. **Mixing up protocols**: Distinguishing between 2PC, 3PC, Paxos, Raft
4. **Misunderstanding trade-offs**: Knowing when each consistency model is appropriate
5. **Forgetting failure models**: Remembering the different types of failures systems must handle
6. **Confusing architectures**: Distinguishing between client-server, peer-to-peer, microservices
7. **Mixing up consistency models**: Knowing the differences between linearizability, sequential, causal, eventual
8. **Overlooking real-world constraints**: Remembering that theoretical ideals often need adjustment in practice

## Summary

This chapter has provided a comprehensive review of all the key concepts covered in the Distributed Systems subject. By understanding the fundamentals, communication mechanisms, consistency models, replication and partitioning strategies, transaction and consensus protocols, fault tolerance techniques, storage systems, caching and messaging approaches, scalability and load balancing methods, CAP PACELC trade-offs, and real-world implementations, you should be well-prepared for interviews and practical work in distributed systems.

Remember that distributed systems are fundamentally about trade-offs—between consistency and availability, performance and correctness, simplicity and functionality. The best distributed systems make informed trade-offs based on their specific requirements and constraints, rather than trying to optimize for all properties simultaneously.

Good luck with your interview preparation and continued learning in the fascinating field of distributed systems!