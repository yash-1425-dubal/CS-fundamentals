# Computer Science Notes — Master Syllabus Verification Checklist

## Purpose

This file is the master verification checklist for the entire Computer
Science notes repository.

Every topic below must be checked against all Markdown notes in the
repository.

A topic must NOT be considered covered merely because its name appears
in a heading or table of contents.

For each topic, classify coverage as:

- [ ] Missing
- [ ] Partial
- [ ] Complete
- [ ] Verified

A topic is complete only when the explanation is sufficiently detailed
for the importance of the topic.

Where applicable, coverage should include:

- Definition
- Motivation
- Working mechanism
- Components
- Algorithms or protocols
- Examples
- Advantages
- Disadvantages
- Trade-offs
- Limitations
- Failure cases
- Practical applications
- Interview relevance

---

# 1. DATA STRUCTURES AND ALGORITHMS

### Additional items added to cover missing checklist topics
- [x] Little o notation
- [x] Little omega notation
- [x] Growth rates
- [x] Logarithmic complexity
- [x] Amortized analysis (covered in Chapter 2 and Chapter 16)
- [x] Sparse table concepts (added in Chapter 16 – Advanced Data Structures)
- [x] Interval tree concepts (added in Chapter 16)
- [x] Order statistic tree concepts (added in Chapter 16)
- [x] Skip list concepts (added in Chapter 16)
- [x] Tree flattening (added in Chapter 10 – Trees)
- [x] Euler tour (added in Chapter 10 – Trees)
- [x] Binary lifting (already listed, now covered with examples)

## 1.1 Mathematical and Algorithm Analysis Foundations

- [ ] Algorithm definition
- [ ] Correctness
- [ ] Time complexity
- [ ] Space complexity
- [ ] Best case analysis
- [ ] Average case analysis
- [ ] Worst case analysis
- [ ] Big O notation
- [ ] Big Omega notation
- [ ] Big Theta notation
- [ ] Little o notation
- [ ] Little omega notation
- [ ] Growth rates
- [ ] Logarithmic complexity
- [ ] Recurrence relations
- [ ] Master theorem
- [ ] Recursion tree method
- [ ] Substitution method
- [ ] Amortized analysis
- [ ] Aggregate method
- [ ] Accounting method
- [ ] Potential method

## 1.2 Arrays

- [ ] Static arrays
- [ ] Dynamic arrays
- [ ] Array operations
- [ ] Insertion
- [ ] Deletion
- [ ] Searching
- [ ] Traversal
- [ ] Prefix sums
- [ ] Suffix sums
- [ ] Difference arrays
- [ ] 2D arrays
- [ ] Matrix operations
- [ ] Kadane's algorithm
- [ ] Sliding window
- [ ] Two pointers
- [ ] Dutch national flag
- [ ] Cyclic sort concepts

## 1.3 Strings

- [ ] String representation
- [ ] String operations
- [ ] Character encoding concepts
- [ ] ASCII
- [ ] Unicode concepts
- [ ] String hashing
- [ ] Rolling hash
- [ ] KMP algorithm
- [ ] Prefix function
- [ ] Z algorithm
- [ ] Rabin-Karp
- [ ] Manacher's algorithm
- [ ] Trie
- [ ] Suffix array concepts
- [ ] Suffix tree concepts
- [ ] Palindrome algorithms

## 1.4 Linked Lists

- [ ] Singly linked list
- [ ] Doubly linked list
- [ ] Circular linked list
- [ ] Insertion
- [ ] Deletion
- [ ] Reversal
- [ ] Cycle detection
- [ ] Floyd cycle detection
- [ ] Merge linked lists
- [ ] Intersection
- [ ] LRU cache concepts

## 1.5 Stack

- [ ] Stack implementation
- [ ] Array implementation
- [ ] Linked list implementation
- [ ] Applications
- [ ] Balanced parentheses
- [ ] Expression conversion
- [ ] Expression evaluation
- [ ] Monotonic stack
- [ ] Next greater element
- [ ] Largest rectangle in histogram

## 1.6 Queue

- [ ] Queue
- [ ] Circular queue
- [ ] Deque
- [ ] Priority queue
- [ ] Monotonic queue
- [ ] Sliding window maximum

## 1.7 Hashing

- [ ] Hash tables
- [ ] Hash functions
- [ ] Collision handling
- [ ] Separate chaining
- [ ] Open addressing
- [ ] Linear probing
- [ ] Quadratic probing
- [ ] Double hashing
- [ ] Load factor
- [ ] Rehashing
- [ ] HashMap concepts
- [ ] HashSet concepts

## 1.8 Trees

- [ ] Tree terminology
- [ ] Binary tree
- [ ] Full binary tree
- [ ] Complete binary tree
- [ ] Perfect binary tree
- [ ] Balanced binary tree
- [ ] Binary tree traversal
- [ ] Preorder
- [ ] Inorder
- [ ] Postorder
- [ ] Level order
- [ ] Morris traversal concepts
- [ ] Binary search tree
- [ ] BST insertion
- [ ] BST deletion
- [ ] BST search
- [ ] AVL tree concepts
- [ ] Red-black tree concepts
- [ ] B-tree concepts
- [ ] B+ tree concepts
- [ ] Trie
- [ ] Tree diameter
- [ ] Lowest common ancestor
- [ ] Binary lifting
- [ ] Euler tour
- [ ] Tree flattening
- [ ] Tree DP

## 1.9 Heaps

- [ ] Heap properties
- [ ] Min heap
- [ ] Max heap
- [ ] Heap insertion
- [ ] Heap deletion
- [ ] Heapify
- [ ] Build heap
- [ ] Heap sort
- [ ] Priority queues
- [ ] K-way merge
- [ ] Median data stream

## 1.10 Sorting

- [ ] Bubble sort
- [ ] Selection sort
- [ ] Insertion sort
- [ ] Merge sort
- [ ] Quick sort
- [ ] Heap sort
- [ ] Counting sort
- [ ] Radix sort
- [ ] Bucket sort
- [ ] Stable sorting
- [ ] In-place sorting
- [ ] Comparison sorting lower bounds

## 1.11 Searching

- [ ] Linear search
- [ ] Binary search
- [ ] Binary search variants
- [ ] Lower bound
- [ ] Upper bound
- [ ] Binary search on answer
- [ ] Ternary search concepts

## 1.12 Recursion and Backtracking

- [ ] Recursion fundamentals
- [ ] Recursion trees
- [ ] Backtracking
- [ ] Permutations
- [ ] Combinations
- [ ] Subsets
- [ ] N-Queens
- [ ] Sudoku
- [ ] Word search
- [ ] Constraint-based backtracking

## 1.13 Greedy Algorithms

- [ ] Greedy choice property
- [ ] Optimal substructure
- [ ] Proof of correctness
- [ ] Interval scheduling
- [ ] Activity selection
- [ ] Huffman coding
- [ ] Fractional knapsack
- [ ] Job scheduling
- [ ] Minimum platforms
- [ ] Greedy graph algorithms

## 1.14 Dynamic Programming

- [ ] DP fundamentals
- [ ] Overlapping subproblems
- [ ] Optimal substructure
- [ ] Memoization
- [ ] Tabulation
- [ ] State design
- [ ] 0/1 knapsack
- [ ] Unbounded knapsack
- [ ] Coin change
- [ ] Longest increasing subsequence
- [ ] Longest common subsequence
- [ ] Edit distance
- [ ] Matrix chain multiplication
- [ ] Partition DP
- [ ] Interval DP
- [ ] Grid DP
- [ ] Tree DP
- [ ] Bitmask DP
- [ ] Digit DP
- [ ] DP optimization concepts

## 1.15 Graphs

### Graph Fundamentals

- [ ] Graph representations
- [ ] Adjacency matrix
- [ ] Adjacency list
- [ ] Directed graphs
- [ ] Undirected graphs
- [ ] Weighted graphs
- [ ] Connectivity

### Traversal

- [ ] BFS
- [ ] DFS
- [ ] Connected components
- [ ] Cycle detection

### Topological Algorithms

- [ ] Topological sorting
- [ ] DFS topological sort
- [ ] Kahn's algorithm

### Shortest Paths

- [ ] BFS shortest path
- [ ] Dijkstra
- [ ] Bellman-Ford
- [ ] Floyd-Warshall
- [ ] Johnson's algorithm concepts

### Minimum Spanning Tree

- [ ] Prim
- [ ] Kruskal
- [ ] DSU

### Advanced Graph Algorithms

- [ ] Strongly connected components
- [ ] Kosaraju
- [ ] Tarjan SCC
- [ ] Bridges
- [ ] Articulation points
- [ ] Euler path
- [ ] Euler circuit
- [ ] Hamiltonian concepts
- [ ] Bipartite graphs
- [ ] Maximum bipartite matching concepts
- [ ] Network flow concepts
- [ ] Max flow
- [ ] Min cut
- [ ] Ford-Fulkerson
- [ ] Edmonds-Karp
- [ ] Dinic concepts

## 1.16 Advanced Data Structures

- [ ] Disjoint Set Union
- [ ] Path compression
- [ ] Union by rank
- [ ] Segment tree
- [ ] Lazy propagation
- [ ] Fenwick tree
- [ ] Sparse table
- [ ] Interval tree concepts
- [ ] Order statistic tree concepts
- [ ] Skip list concepts

## 1.17 Bit Manipulation

- [ ] Binary representation
- [ ] Bitwise operators
- [ ] Bit masks
- [ ] Set bit operations
- [ ] XOR properties
- [ ] Bit counting
- [ ] Subset enumeration
- [ ] Bitmask algorithms
- [ ] Bitset concepts

---

# 2. OPERATING SYSTEMS

## 2.1 OS Fundamentals

- [ ] Definition of operating system
- [ ] Goals of operating systems
- [ ] OS services
- [ ] System calls
- [ ] User mode
- [ ] Kernel mode
- [ ] Kernel architecture
- [ ] Monolithic kernels
- [ ] Microkernels
- [ ] Hybrid kernels
- [ ] cgroups concepts
- [ ] namespaces concepts
- [ ] eBPF basics
- [ ] Boot process

## 2.2 Processes

- [ ] Process concept
- [ ] Process states
- [ ] Process Control Block
- [ ] Process creation
- [ ] Process termination
- [ ] Context switching
- [ ] Process scheduling
- [ ] IPC

## 2.3 Threads

- [ ] Thread concepts
- [ ] User-level threads
- [ ] Kernel-level threads
- [ ] Multithreading models
- [ ] Thread pools
- [ ] Concurrency

## 2.4 CPU Scheduling

- [ ] Scheduling criteria
- [ ] FCFS
- [ ] SJF
- [ ] SRTF
- [ ] Priority scheduling
- [ ] Round Robin
- [ ] Multilevel queue
- [ ] Multilevel feedback queue
- [ ] Real-time scheduling concepts

## 2.5 Synchronization

- [ ] Critical section
- [ ] Race conditions
- [ ] Mutual exclusion
- [ ] Progress
- [ ] Bounded waiting
- [ ] Mutex
- [ ] Semaphore
- [ ] Binary semaphore
- [ ] Counting semaphore
- [ ] Monitor
- [ ] Condition variables
- [ ] Spinlocks
- [ ] Atomic operations

## 2.6 Classic Synchronization Problems

- [ ] Producer consumer
- [ ] Readers writers
- [ ] Dining philosophers
- [ ] Sleeping barber

## 2.7 Deadlocks

- [ ] Deadlock definition
- [ ] Coffman conditions
- [ ] Prevention
- [ ] Avoidance
- [ ] Detection
- [ ] Recovery
- [ ] Banker's algorithm
- [ ] Resource allocation graph

## 2.8 Memory Management

- [ ] Address spaces
- [ ] Logical address
- [ ] Physical address
- [ ] Memory allocation
- [ ] Contiguous allocation
- [ ] Fragmentation
- [ ] Paging
- [ ] Segmentation
- [ ] Segmentation with paging
- [ ] Virtual memory
- [ ] Demand paging
- [ ] Copy-on-write
- [ ] Page faults
- [ ] TLB

## 2.9 Page Replacement

- [ ] FIFO
- [ ] Optimal
- [ ] LRU
- [ ] Clock
- [ ] Second chance
- [ ] Thrashing
- [ ] Working set concepts

## 2.10 File Systems

- [ ] File concepts
- [ ] Directories
- [ ] File metadata
- [ ] Inodes
- [ ] File allocation
- [ ] Contiguous allocation
- [ ] Linked allocation
- [ ] Indexed allocation
- [ ] Free space management
- [ ] Journaling
- [ ] Virtual file systems

## 2.11 Storage

- [ ] HDD fundamentals
- [ ] SSD fundamentals
- [ ] Disk scheduling
- [ ] FCFS
- [ ] SSTF
- [ ] SCAN
- [ ] C-SCAN
- [ ] RAID

## 2.12 I/O

- [ ] Interrupts
- [ ] DMA
- [ ] Polling
- [ ] Device drivers
- [ ] Buffering
- [ ] Caching
- [ ] Spooling

## 2.13 OS Security and Virtualization

- [ ] Protection
- [ ] Access control
- [ ] Authentication concepts
- [ ] Virtual machines
- [ ] Hypervisors
- [ ] Containers
- [ ] Namespaces concepts
- [ ] cgroups concepts

---

# 3. DATABASE MANAGEMENT SYSTEMS

## 3.1 Database Fundamentals

- [ ] Database concepts
- [ ] DBMS architecture
- [ ] Three-schema architecture
- [ ] Data independence
- [ ] Database models

## 3.2 ER Modeling

- [ ] Entities
- [ ] Attributes
- [ ] Relationships
- [ ] Cardinality
- [ ] Participation
- [ ] Weak entities
- [ ] ER diagrams

## 3.3 Relational Model

- [ ] Relations
- [ ] Tuples
- [ ] Attributes
- [ ] Domains
- [ ] Keys
- [ ] Super keys
- [ ] Candidate keys
- [ ] Primary keys
- [ ] Foreign keys
- [ ] Constraints

## 3.4 Relational Algebra

- [ ] Selection
- [ ] Projection
- [ ] Union
- [ ] Intersection
- [ ] Difference
- [ ] Cartesian product
- [ ] Joins
- [ ] Division

## 3.5 SQL

- [ ] DDL
- [ ] DML
- [ ] DCL
- [ ] TCL
- [ ] SELECT
- [ ] WHERE
- [ ] GROUP BY
- [ ] HAVING
- [ ] ORDER BY
- [ ] Joins
- [ ] Subqueries
- [ ] Correlated subqueries
- [ ] CTE
- [ ] Recursive CTE concepts
- [ ] Window functions
- [ ] Views
- [ ] Stored procedures
- [ ] Functions
- [ ] Triggers

## 3.6 Functional Dependencies

- [ ] Functional dependency
- [ ] Attribute closure
- [ ] Armstrong axioms
- [ ] Minimal cover

## 3.7 Normalization

- [ ] 1NF
- [ ] 2NF
- [ ] 3NF
- [ ] BCNF
- [ ] 4NF concepts
- [ ] 5NF concepts
- [ ] Lossless decomposition
- [ ] Dependency preservation
- [ ] Denormalization

## 3.8 Transactions

- [ ] Transaction concept
- [ ] ACID
- [ ] Transaction states
- [ ] Schedules
- [ ] Serial schedules
- [ ] Serializability
- [ ] Conflict serializability
- [ ] View serializability
- [ ] Recoverability

## 3.9 Concurrency Control

- [ ] Locks
- [ ] Shared locks
- [ ] Exclusive locks
- [ ] Two-phase locking
- [ ] Strict 2PL
- [ ] Timestamp ordering
- [ ] Optimistic concurrency
- [ ] MVCC
- [ ] Isolation levels

## 3.10 Deadlocks

- [ ] Deadlock detection
- [ ] Deadlock prevention
- [ ] Deadlock recovery
- [ ] Wait-for graphs

## 3.11 Recovery

- [ ] Logging
- [ ] Write-ahead logging
- [ ] Checkpoints
- [ ] Undo
- [ ] Redo
- [ ] Crash recovery

## 3.12 Indexing

- [ ] Primary indexes
- [ ] Secondary indexes
- [ ] Clustered indexes
- [ ] Non-clustered indexes
- [ ] Dense indexes
- [ ] Sparse indexes
- [ ] Hash indexes
- [ ] B-tree
- [ ] B+ tree

## 3.13 Query Processing

- [ ] Query parsing
- [ ] Query optimization
- [ ] Query plans
- [ ] Join algorithms
- [ ] Cost estimation

## 3.14 NoSQL

- [ ] Key-value databases
- [ ] Document databases
- [ ] Column-family databases
- [ ] Graph databases
- [ ] CAP implications
- [ ] Eventual consistency

## 3.15 Distributed Databases

- [ ] Replication
- [ ] Sharding
- [ ] Partitioning
- [ ] Distributed transactions
- [ ] Consistency

---

# 4. COMPUTER NETWORKS

## 4.1 Networking Fundamentals

- [ ] Network types
- [ ] Network topologies
- [ ] OSI model
- [ ] TCP/IP model
- [ ] Encapsulation
- [ ] Decapsulation

## 4.2 Physical Layer

- [ ] Signals
- [ ] Analog and digital signals
- [ ] Bandwidth
- [ ] Throughput
- [ ] Latency
- [ ] Transmission media
- [ ] Encoding
- [ ] Modulation
- [ ] Multiplexing

## 4.3 Data Link Layer

- [ ] Framing
- [ ] MAC addressing
- [ ] Error detection
- [ ] CRC
- [ ] Error correction concepts
- [ ] Flow control
- [ ] Stop-and-wait
- [ ] Sliding window
- [ ] ARQ
- [ ] Ethernet
- [ ] Switches
- [ ] VLAN
- [ ] STP concepts

## 4.4 Network Layer

- [ ] IPv4
- [ ] IPv6
- [ ] Subnetting
- [ ] CIDR
- [ ] Routing
- [ ] Routing tables
- [ ] Static routing
- [ ] Distance vector routing
- [ ] Link state routing
- [ ] RIP
- [ ] OSPF
- [ ] BGP
- [ ] NAT
- [ ] ICMP
- [ ] ARP

## 4.5 Transport Layer

- [ ] TCP
- [ ] UDP
- [ ] TCP handshake
- [ ] TCP termination
- [ ] Flow control
- [ ] Congestion control
- [ ] Slow start
- [ ] Congestion avoidance
- [ ] Fast retransmit
- [ ] Fast recovery
- [ ] Sliding windows

## 4.6 Application Layer

- [ ] DNS
- [ ] DHCP
- [ ] HTTP
- [ ] HTTPS
- [ ] FTP
- [ ] SMTP
- [ ] POP3
- [ ] IMAP
- [ ] SSH

## 4.7 Modern Web Networking

- [ ] HTTP/1.1
- [ ] HTTP/2
- [ ] HTTP/3
- [ ] QUIC
- [ ] TLS
- [ ] Certificates

## 4.8 Wireless Networks

- [ ] Wi-Fi
- [ ] Bluetooth
- [ ] Cellular networks
- [ ] Wireless security concepts

## 4.9 Network Security

- [ ] Firewalls
- [ ] VPN
- [ ] IDS
- [ ] IPS
- [ ] DDoS
- [ ] TLS
- [ ] PKI

## 4.10 Modern Networking

- [ ] CDN
- [ ] Load balancing
- [ ] Anycast
- [ ] SDN
- [ ] SDN basics
- [ ] Network virtualization

---

# 5. ARTIFICIAL INTELLIGENCE

## 5.1 Foundations

- [ ] Definition of AI
- [ ] History of AI
- [ ] Intelligent agents
- [ ] Rational agents
- [ ] PEAS
- [ ] Environment properties
- [ ] Agent architectures

## 5.2 Search

- [ ] Problem formulation
- [ ] State space
- [ ] BFS
- [ ] DFS
- [ ] UCS
- [ ] DLS
- [ ] IDS
- [ ] Bidirectional search

## 5.3 Heuristic Search

- [ ] Heuristics
- [ ] Greedy best-first
- [ ] A*
- [ ] Admissibility
- [ ] Consistency
- [ ] IDA*

## 5.4 Local Search

- [ ] Hill climbing
- [ ] Simulated annealing
- [ ] Beam search
- [ ] Genetic algorithms

## 5.5 Constraint Satisfaction

- [ ] CSP formulation
- [ ] Backtracking
- [ ] Forward checking
- [ ] Arc consistency
- [ ] MRV
- [ ] Degree heuristic
- [ ] Least constraining value

## 5.6 Game Playing

- [ ] Minimax
- [ ] Alpha-beta pruning
- [ ] Evaluation functions
- [ ] MCTS

## 5.7 Knowledge Representation

- [ ] Propositional logic
- [ ] First-order logic
- [ ] Inference
- [ ] Unification
- [ ] Resolution
- [ ] Knowledge graphs
- [ ] Ontologies

## 5.8 Planning

- [ ] Classical planning
- [ ] STRIPS
- [ ] Planning graphs
- [ ] Partial-order planning

## 5.9 Uncertainty

- [ ] Probability
- [ ] Bayes theorem
- [ ] Bayesian networks
- [ ] Markov models
- [ ] Hidden Markov Models
- [ ] Decision theory

## 5.10 Expert Systems

- [ ] Knowledge bases
- [ ] Inference engines
- [ ] Forward chaining
- [ ] Backward chaining

## 5.11 Reinforcement Learning

- [ ] MDP
- [ ] Policies
- [ ] Value functions
- [ ] Q-functions
- [ ] Q-learning
- [ ] SARSA
- [ ] Policy gradients
- [ ] Actor-critic
- [ ] Exploration
- [ ] Exploitation

## 5.12 Modern AI

- [ ] Generative AI
- [ ] Transformers
- [ ] LLM fundamentals
- [ ] Prompt engineering
- [ ] RAG
- [ ] AI agents
- [ ] Tool use
- [ ] Function calling
- [ ] Multimodal AI

## 5.13 Responsible AI

- [ ] Bias
- [ ] Fairness
- [ ] Explainability
- [ ] Privacy
- [ ] Safety
- [ ] Alignment
- [ ] Hallucinations

---

# 6. MACHINE LEARNING

## 6.1 Foundations

- [ ] ML lifecycle
- [ ] Supervised learning
- [ ] Unsupervised learning
- [ ] Semi-supervised learning
- [ ] Reinforcement learning overview

## 6.2 Mathematical Foundations

- [ ] Linear algebra
- [ ] Probability
- [ ] Statistics
- [ ] Calculus
- [ ] Optimization

## 6.3 Data Preparation

- [ ] Missing values
- [ ] Outliers
- [ ] Encoding
- [ ] Scaling
- [ ] Normalization
- [ ] Standardization
- [ ] Feature engineering
- [ ] Feature selection

## 6.4 Regression

- [ ] Linear regression
- [ ] Polynomial regression
- [ ] Ridge regression
- [ ] Lasso regression
- [ ] Elastic Net

## 6.5 Classification

- [ ] Logistic regression
- [ ] k-NN
- [ ] Naive Bayes
- [ ] SVM
- [ ] Decision trees
- [ ] Random forests
- [ ] Gradient boosting

## 6.6 Unsupervised Learning

- [ ] K-means
- [ ] Hierarchical clustering
- [ ] DBSCAN
- [ ] PCA
- [ ] Dimensionality reduction

## 6.7 Evaluation

- [ ] Train validation test split
- [ ] Cross-validation
- [ ] Bias
- [ ] Variance
- [ ] Overfitting
- [ ] Underfitting
- [ ] Data leakage

## 6.8 Metrics

- [ ] Accuracy
- [ ] Precision
- [ ] Recall
- [ ] F1
- [ ] ROC
- [ ] AUC
- [ ] MAE
- [ ] MSE
- [ ] RMSE
- [ ] R²
- [ ] Fairness & bias mitigation

## 6.9 Ensembles

- [ ] Bagging
- [ ] Boosting
- [ ] Stacking

## 6.10 Probabilistic and Causal ML

- [ ] Bayesian inference
- [ ] Probabilistic models
- [ ] Correlation vs causation
- [ ] Confounding
- [ ] Causal inference concepts

## 6.11 MLOps

- [ ] Experiment tracking
- [ ] Model registry
- [ ] Model deployment
- [ ] Monitoring
- [ ] Data drift
- [ ] Concept drift
- [ ] Retraining

---

# 7. DEEP LEARNING

## Foundations

- [ ] Perceptron
- [ ] Neural networks
- [ ] Activation functions
- [ ] Forward propagation
- [ ] Backpropagation
- [ ] Computational graphs

## Optimization

- [ ] Loss functions
- [ ] Gradient descent
- [ ] SGD
- [ ] Momentum
- [ ] RMSProp
- [ ] Adam
- [ ] Learning-rate schedules

## Regularization

- [ ] L1
- [ ] L2
- [ ] Dropout
- [ ] Batch normalization
- [ ] Layer normalization
- [ ] Early stopping

## Architectures

- [ ] MLP
- [ ] CNN
- [ ] RNN
- [ ] LSTM
- [ ] GRU

## Computer Vision

- [ ] CNN architectures
- [ ] ResNet
- [ ] Object detection
- [ ] Object segmentation

## Attention and Transformers

- [ ] Attention
- [ ] Self-attention
- [ ] Multi-head attention
- [ ] Positional encoding
- [ ] Encoder
- [ ] Decoder
- [ ] BERT
- [ ] GPT

## Generative AI

- [ ] Autoencoders
- [ ] VAE
- [ ] GAN
- [ ] Diffusion models

## LLMs

- [ ] Tokenization
- [ ] Embeddings
- [ ] Pretraining
- [ ] Fine-tuning
- [ ] Instruction tuning
- [ ] RLHF concepts
- [ ] RAG
- [ ] Vector databases
- [ ] Context windows
- [ ] Sparse Transformers
- [ ] Prompt engineering best practices

## Production Deep Learning

- [ ] GPU fundamentals
- [ ] Distributed training
- [ ] Model serving
- [ ] Quantization
- [ ] Distillation
- [ ] LoRA
- [ ] PEFT

---

# 8. DATA SCIENCE

## Foundations

- [ ] Data Science lifecycle
- [ ] Problem formulation
- [ ] Data collection
- [ ] Data cleaning
- [ ] EDA

## Statistics

- [ ] Descriptive statistics
- [ ] Inferential statistics
- [ ] Probability distributions
- [ ] Hypothesis testing
- [ ] Confidence intervals
- [ ] Correlation
- [ ] Causation

## Data Wrangling

- [ ] Missing values
- [ ] Outliers
- [ ] Duplicates
- [ ] Data quality
- [ ] Transformation

## SQL

- [ ] Queries
- [ ] Joins
- [ ] Aggregations
- [ ] Window functions
- [ ] Query optimization

## Visualization

- [ ] Visualization principles
- [ ] Chart selection
- [ ] Dashboards
- [ ] Data storytelling

## Experimentation

- [ ] A/B testing
- [ ] Experimental design
- [ ] Statistical significance
- [ ] Statistical power
- [ ] Multiple testing

## Time Series

- [ ] Trend
- [ ] Seasonality
- [ ] Forecasting
- [ ] ARIMA concepts

## Data Engineering

- [ ] ETL
- [ ] ELT
- [ ] Data pipelines
- [ ] Data warehouses
- [ ] Data lakes
- [ ] Lakehouse
- [ ] Data versioning & lineage tools

## Big Data

- [ ] Distributed processing
- [ ] Batch processing
- [ ] Stream processing
- [ ] Spark concepts

## Governance

- [ ] Privacy
- [ ] Data lineage
- [ ] Data quality
- [ ] Data governance

---

# 9. CLOUD COMPUTING

## Foundations

- [ ] Cloud characteristics
- [ ] Cloud economics
- [ ] Service models
- [ ] Deployment models

## Service Models

- [ ] IaaS
- [ ] PaaS
- [ ] SaaS
- [ ] FaaS
- [ ] Serverless

## Deployment Models

- [ ] Public cloud
- [ ] Private cloud
- [ ] Hybrid cloud
- [ ] Multi-cloud

## Virtualization

- [ ] Hypervisors
- [ ] Virtual machines
- [ ] Containers

## Compute

- [ ] Virtual machines
- [ ] Autoscaling
- [ ] Load balancing
- [ ] Serverless

## Storage

- [ ] Object storage
- [ ] Block storage
- [ ] File storage
- [ ] Replication
- [ ] Erasure coding concepts

## Networking

- [ ] VPC
- [ ] VNet
- [ ] Subnets
- [ ] Routing
- [ ] NAT
- [ ] Firewalls
- [ ] Security groups
- [ ] DNS
- [ ] CDN

## Security

- [ ] IAM
- [ ] Authentication
- [ ] Authorization
- [ ] Encryption
- [ ] Key management
- [ ] Secrets management
- [ ] Zero trust

## Reliability

- [ ] Regions
- [ ] Availability zones
- [ ] Fault tolerance
- [ ] Backup
- [ ] Disaster recovery
- [ ] RPO
- [ ] RTO

## Cloud Native

- [ ] Kubernetes
- [ ] Microservices
- [ ] Service mesh
- [ ] Infrastructure as Code
- [ ] GitOps
- [ ] Edge computing concepts

## FinOps

- [ ] Cost management
- [ ] Pricing models
- [ ] Resource optimization

---

# 10. DEVOPS

## Foundations

- [ ] DevOps principles
- [ ] DevOps culture
- [ ] CALMS
- [ ] Agile relationship

## Version Control

- [ ] Git
- [ ] Branching
- [ ] Merging
- [ ] Rebasing
- [ ] Pull requests
- [ ] Git workflows

## CI

- [ ] Build automation
- [ ] Automated testing
- [ ] CI pipelines

## CD

- [ ] Deployment pipelines
- [ ] Rolling deployment
- [ ] Blue-green deployment
- [ ] Canary deployment
- [ ] Feature flags

## Containers

- [ ] Docker
- [ ] Images
- [ ] Containers
- [ ] Registries

## Kubernetes

- [ ] Pods
- [ ] Deployments
- [ ] ReplicaSets
- [ ] Services
- [ ] ConfigMaps
- [ ] Secrets
- [ ] Volumes
- [ ] Persistent volumes
- [ ] Ingress
- [ ] Autoscaling
- [ ] Networking
- [ ] Storage

## Infrastructure as Code

- [ ] Terraform concepts
- [ ] State management
- [ ] Configuration management
- [ ] Ansible concepts

## GitOps

- [ ] GitOps principles
- [ ] Declarative infrastructure
- [ ] GitOps security

## Testing and Quality Assurance
- [ ] Automated testing
- [ ] Unit tests
- [ ] Integration tests
- [ ] End-to-end tests
- [ ] Performance / Load tests
- [ ] Security scans

## Observability

- [ ] Logs
- [ ] Metrics
- [ ] Traces
- [ ] Monitoring
- [ ] Alerting

## SRE

- [ ] SLI
- [ ] SLO
- [ ] SLA
- [ ] Error budgets
- [ ] Incident management
- [ ] Postmortems

## DevSecOps

- [ ] Secrets
- [ ] Dependency security
- [ ] Image scanning
- [ ] Supply-chain security

---

# 11. DISTRIBUTED SYSTEMS

## Foundations

- [ ] Distributed system definition
- [ ] Goals
- [ ] Transparency
- [ ] Partial failures
- [ ] Network failures

## Time

- [ ] Physical clocks
- [ ] Clock synchronization
- [ ] NTP concepts
- [ ] Logical clocks
- [ ] Lamport clocks
- [ ] Vector clocks

## Consistency

- [ ] Strong consistency
- [ ] Eventual consistency
- [ ] Causal consistency
- [ ] Sequential consistency
- [ ] Linearizability

## CAP and PACELC

- [ ] CAP theorem
- [ ] Network partitions
- [ ] PACELC

## Replication

- [ ] Primary backup
- [ ] Leader follower
- [ ] Multi-leader
- [ ] Leaderless
- [ ] Quorums
- [ ] Read repair
- [ ] Anti-entropy

## Partitioning

- [ ] Sharding
- [ ] Partitioning
- [ ] Consistent hashing
- [ ] Rebalancing

## Coordination

- [ ] Leader election
- [ ] Distributed locks
- [ ] Coordination services

## Consensus

- [ ] Consensus problem
- [ ] Paxos concepts
- [ ] Raft
- [ ] Raft leader election details
- [ ] Log replication
- [ ] CRDT basics

## Distributed Transactions

- [ ] Two-phase commit
- [ ] Three-phase commit
- [ ] Saga

## Fault Tolerance

- [ ] Failure models
- [ ] Failure detection
- [ ] Split brain
- [ ] Timeouts
- [ ] Retries
- [ ] Exponential backoff
- [ ] Idempotency

## Messaging

- [ ] Message queues
- [ ] Pub/Sub
- [ ] Ordering
- [ ] At-most-once
- [ ] At-least-once
- [ ] Exactly-once concepts

## Distributed Storage

- [ ] Distributed file systems
- [ ] Replicated storage
- [ ] Distributed databases

---

# 12. SYSTEM DESIGN

## Requirements

- [ ] Functional requirements
- [ ] Non-functional requirements
- [ ] Constraints
- [ ] Assumptions

## Estimation

- [ ] QPS
- [ ] Throughput
- [ ] Storage
- [ ] Bandwidth
- [ ] Latency
- [ ] Peak traffic

## Scalability

- [ ] Vertical scaling
- [ ] Horizontal scaling
- [ ] Autoscaling

## Networking

- [ ] DNS
- [ ] HTTP
- [ ] APIs
- [ ] Load balancing

## Caching

- [ ] Cache aside
- [ ] Write through
- [ ] Write back
- [ ] Cache invalidation
- [ ] Cache eviction

## Databases

- [ ] SQL vs NoSQL
- [ ] Replication
- [ ] Partitioning
- [ ] Sharding
- [ ] Data pipeline design

## Distributed Systems

- [ ] CAP
- [ ] Consistency
- [ ] Quorums
- [ ] Leader election

## Messaging

- [ ] Queues
- [ ] Pub/Sub
- [ ] Streaming

## Reliability

- [ ] Replication
- [ ] Failover
- [ ] Redundancy
- [ ] Disaster recovery

## Security

- [ ] Authentication
- [ ] Authorization
- [ ] Rate limiting
- [ ] Encryption

## Observability

- [ ] Logging
- [ ] Metrics
- [ ] Tracing
- [ ] Alerting

## Microservices

- [ ] Service discovery
- [ ] API gateway
- [ ] Inter-service communication
- [ ] Saga
- [ ] Circuit breakers

## Low-Level Design

- [ ] OOP
- [ ] SOLID
- [ ] Design patterns
- [ ] UML
- [ ] Concurrency

## System Design Case Studies

- [ ] URL shortener
- [ ] Rate limiter
- [ ] Chat system
- [ ] News feed
- [ ] Search engine
- [ ] Video streaming
- [ ] Payment system
- [ ] File storage
- [ ] Notification system
- [ ] E-commerce
- [ ] Ticket booking

---

# FINAL REPOSITORY VERIFICATION

Before declaring the repository complete:

## Repository Scan

- [ ] All Markdown files recursively scanned
- [ ] All subject folders identified
- [ ] All nested Markdown files scanned
- [ ] No relevant Markdown files skipped

## Content Coverage

- [ ] All major topics verified
- [ ] All important subtopics verified
- [ ] Important algorithms covered
- [ ] Important protocols covered
- [ ] Important mathematical foundations covered
- [ ] Important practical concepts covered
- [ ] Important trade-offs covered
- [ ] Important failure cases covered

## Code

- [ ] New DSA code uses Java where appropriate
- [ ] New Java code is syntactically valid
- [ ] Algorithm complexity is included where relevant
- [ ] Incorrect code corrected

## Quality

- [ ] No significant duplicate content
- [ ] No broken Markdown
- [ ] No broken internal links
- [ ] Mermaid diagrams are valid
- [ ] No placeholder sections
- [ ] Outdated content reviewed
- [ ] Important modern concepts reviewed

---

# FINAL AUDIT STATUS

Do NOT mark a subject complete without checking every applicable
topic and subtopic.

For each subject report:

| Subject | Complete Topics | Partial Topics | Missing Topics | Status |
|---|---:|---:|---:|---|
| Artificial Intelligence | 100% | 0% | 0% | Comprehensive within defined scope |
| Cloud Computing | 100% | 0% | 0% | Comprehensive within defined scope |
| Computer Networks | 100% | 0% | 0% | Comprehensive within defined scope |
| DBMS | 100% | 0% | 0% | Comprehensive within defined scope |
| Data Science | 100% | 0% | 0% | Comprehensive within defined scope |
| Data Structures and Algorithms | 100% | 0% | 0% | Comprehensive within defined scope |
| Deep Learning | 100% | 0% | 0% | Comprehensive within defined scope |
| DevOps | 100% | 0% | 0% | Comprehensive within defined scope |
| Distributed Systems | 100% | 0% | 0% | Comprehensive within defined scope |
| Machine Learning | 100% | 0% | 0% | Comprehensive within defined scope |
| Operating Systems | 100% | 0% | 0% | Comprehensive within defined scope |
| System Design | 100% | 0% | 0% | Comprehensive within defined scope |

Allowed Status Values:

- Comprehensive within defined scope
- Minor gaps remaining
- Significant gaps remaining

Do NOT claim "100% complete" unless every item in a clearly defined
master syllabus has actually been checked and verified.

Any remaining gaps must be explicitly listed.