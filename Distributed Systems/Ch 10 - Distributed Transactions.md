# Chapter 10: Distributed Transactions

## Introduction

Distributed transactions extend the concept of ACID transactions to distributed systems, enabling operations that span multiple nodes while maintaining consistency guarantees. This chapter covers distributed transaction models, protocols, and related concepts.

## Why Do We Need Distributed Transactions?

Distributed transactions are needed because:

1. **Data consistency**: Ensuring consistency across multiple data stores
2. **Application correctness**: Multi-step operations that must succeed or fail together
3. **Inventory management**: Preventing overselling in e-commerce systems
4. **Financial transfers**: Ensuring money is neither lost nor duplicated
5. **Order processing**: Coordinating payment, inventory, and shipping
6. **Microservices**: Enabling transactions across service boundaries
7. **Audit trails**: Maintaining consistent logs across systems
8. **Regulatory compliance**: Meeting consistency requirements for regulated industries

## Core Concepts

### ACID Properties in Distributed Systems

- **Atomicity**: Transaction either completes fully or has no effect
- **Consistency**: Transaction brings system from one valid state to another
- **Isolation**: Concurrent transactions don't interfere with each other
- **Durability**: Committed transactions survive failures

### Transaction Models

- **Flat transactions**: Single-level transactions with no nesting
- **Nested transactions**: Transactions that contain sub-transactions
- **Distributed transactions**: Transactions that span multiple nodes
- **Workflow transactions**: Long-running transactions modeled as workflows
- **Saga transactions**: Sequence of local transactions with compensating actions

### Transaction Protocols

- **Two-phase commit (2PC)**: Coordinated atomic commit protocol
- **Three-phase commit (3PC)**: Non-blocking variant of 2PC
- **Paxos Commit**: Consensus-based commit protocol
- **Raft Commit**: Raft-based commit protocol
- **Saga protocol**: Compensation-based transaction model

### Transaction Participants

- **Coordinator/Transaction manager**: Coordinates the commit process
- **Participants/Resource managers**: Manage local resources and data
- **Transaction branches**: Local portions of distributed transaction
- **Leaf nodes**: Participants that don't coordinate further transactions

### Transaction States

- **Active**: Transaction is executing
- **Partially committed**: Prepared to commit but waiting for coordination
- **Committed**: Transaction has successfully committed
- **Aborted**: Transaction has been rolled back
- **In-doubt**: Uncertain about commit/abort decision (2PC blocking state)

## How It Works

Distributed transactions work by:

1. **Begin transaction**: Application starts a distributed transaction
2. **Execute operations**: Perform local operations at each participant
3. **Prepare phase**: Coordinator asks participants to prepare for commit
4. **Vote collection**: Participants vote yes/no based on local readiness
5. **Decision phase**: Coordinator decides commit or abort based on votes
6. **Execution phase**: Coordinator tells participants to commit or abort
7. **Completion**: Participants acknowledge completion
8. **Recovery**: Handle failures during any phase

## Architecture

Different architectural approaches to distributed transactions:

### Coordinator-Based Architecture

- Central coordinator manages transaction lifecycle
- Simple to understand and implement
- Single point of failure (coordinator)
- Examples: Traditional 2PC implementations

### Peer-to-Peer Architecture

- No central coordinator; participants negotiate directly
- More complex but eliminates coordinator bottleneck
- Examples: Some blockchain consensus protocols

### Hierarchical Architecture

- Coordinators organized in a tree structure
- Reduces coordinator bottleneck
- Examples: Some middleware transaction monitors

### Decentralized Architecture

- No central authority; consensus-based approaches
- Examples: Paxos Commit, Raft Commit, blockchain-based transactions

## Algorithms

### Two-Phase Commit (2PC) Algorithm

**Phase 1: Prepare/Voting**
1. Coordinator sends "prepare" to all participants
2. Participants execute transaction locally up to commit point
3. Participants record undo/redo information in durable storage
4. Participants vote "yes" (prepared to commit) or "no" (must abort)
5. Participants send vote to coordinator

**Phase 2: Commit/Abort**
1. Coordinator collects all votes
2. If all votes are "yes": send "commit" to all participants
3. If any vote is "no": send "abort" to all participants
4. Participants execute decision locally:
   - If "commit": make changes permanent, release locks
   - If "abort": undo changes using undo log, release locks
5. Participants send acknowledgment to coordinator
6. Coordinator records final outcome

### Three-Phase Commit (3PC) Algorithm

**Phase 1: CanCommit**
1. Coordinator sends "canCommit" to participants
2. Participants vote "yes" if they can commit, "no" otherwise
3. Participants send vote to coordinator

**Phase 2: PreCommit**
1. Coordinator decides based on votes:
   - If all "yes": send "preCommit" to all
   - If any "no": send "abort" to all
2. Participants prepare to commit upon receiving "preCommit"
3. Participants acknowledge "preCommit"

**Phase 3: DoCommit**
1. Coordinator sends "doCommit" to all participants
2. Participants make changes permanent
3. Participants send acknowledgment to coordinator
4. Coordinator records completion

### Paxos Commit Algorithm

1. **Prepare phase**: Participants agree to consider committing
2. **Propose phase**: Coordinator proposes commit value
3. **Accept phase**: Participants accept the proposal
4. **Decide phase**: Coordinator decides outcome based on acceptance
5. **Execute phase**: Participants execute the decision

### Saga Pattern Algorithm

1. **Execution phase**: Execute local transactions in sequence
2. **Compensation trigger**: If any transaction fails, initiate compensation
3. **Compensation phase**: Execute compensating transactions in reverse order
4. **Completion**: All transactions committed or all compensated

## Example

### Example: Two-Phase Commit in an E-Commerce System

Consider an e-commerce system with:
- Inventory service (manages stock levels)
- Payment service (processes payments)
- Shipping service (arranges delivery)

**Scenario: Successful Purchase**

1. **Begin transaction**: Application starts distributed transaction
2. **Inventory service**: 
   - Checks if item in stock
   - Reserves item (decrements available count)
   - Prepares to commit (records undo/redo info)
3. **Payment service**:
   - Processes credit card payment
   - Records transaction in pending state
   - Prepares to commit
4. **Shipping service**:
   - Creates shipping label
   - Schedules pickup
   - Prepares to commit
5. **Coordinator**: 
   - Sends "prepare" to all services
   - Receives "yes" votes from all
   - Decides to commit
   - Sends "commit" to all services
6. **Inventory service**: Makes reservation permanent
7. **Payment service**: Marks payment as completed
8. **Shipping service**: Confirms shipment scheduling
9. **All services**: Send acknowledgment to coordinator
10. **Coordinator**: Records transaction as committed

**Scenario: Failed Payment**

1. **Begin transaction**: Application starts distributed transaction
2. **Inventory service**: 
   - Checks stock, reserves item, prepares to commit
3. **Payment service**:
   - Attempts to process credit card
   - Card declined, cannot proceed
   - Votes "no" (must abort)
4. **Coordinator**: 
   - Sends "prepare" to all services
   - Receives "yes" from inventory, "no" from payment
   - Decides to abort (due to "no" vote)
   - Sends "abort" to all services
5. **Inventory service**: 
   - Receives "abort", undoes reservation (restores stock)
6. **Payment service**: 
   - Receives "abort", no action needed (payment not processed)
7. **Shipping service**: 
   - Receives "abort", no action needed (shipping not scheduled)
8. **All services**: Send acknowledgment to coordinator
9. **Coordinator**: Records transaction as aborted

### How It Works

In 2PC:
- Coordinator ensures all-or-nothing behavior
- Participants prepare by making changes durable but not visible
- Decision based on unanimous agreement to proceed
- Failures during protocol require recovery mechanisms to resolve in-doubt states

## Advantages

1. **Atomicity guarantee**: Transaction either fully succeeds or has no effect
2. **Consistency maintenance**: Preserves data consistency across nodes
3. **Isolation**: Concurrent transactions don't interfere (depends on isolation level)
4. **Durability**: Committed transactions survive failures
5. **Application simplicity**: Programmers can reason about transactions as units
6. **Standard protocols**: Well-understood algorithms like 2PC and 3PC
7. **Widespread support**: Available in many databases and middleware systems
8. **Recovery mechanisms**: Protocols include failure handling and recovery

## Disadvantages

1. **Blocking problem**: 2PC can block if coordinator fails after prepare phase
2. **Performance overhead**: Multiple rounds of communication increase latency
3. **Single point of failure**: Coordinator failure can block entire transaction
4. **Complexity**: More complex to implement and manage than local transactions
5. **Scalability limits**: Coordination overhead limits throughput
6. **Availability impact**: Transactions may be unavailable during coordinator failure
7. **Resource locking**: Resources may be locked for extended periods
8. **Failure recovery**: Recovering from failures can be complex and time-consuming

## Limitations

1. **CAP theorem**: Distributed transactions affect availability during partitions
2. **Performance cost**: 2PC typically adds significant latency
3. **Scalability bottleneck**: Coordinator can become performance bottleneck
4. **Failure handling**: Recovering from coordinator failures is complex
5. **Network sensitivity**: Performance degrades with network latency
6. **Heterogeneity challenges**: Different systems may have different transaction models
7. **Long-running transactions**: Traditional protocols don't work well for long transactions
8. **Semantic conflicts**: Applying business logic during compensation can be difficult

## Failure Cases

1. **Coordinator failure**: Coordinator crashes during commit process
2. **Participant failure**: Participant crashes after voting but before decision
3. **Network partition**: Coordinator and participants become isolated
4. **Message loss**: Prepare/commit/abort messages lost in transit
5. **Message duplication**: Duplicate messages cause incorrect processing
6. **Timeouts**: Participants or coordinator fail to respond in time
7. **Disk failure**: Persistent storage fails during transaction
8. **Byzantine failure**: Participant behaves arbitrarily or maliciously
9. **In-doubt transactions**: Transactions left uncertain after coordinator failure
10. **Resource exhaustion**: System runs out of resources to handle transactions

## Trade-offs

1. **Blocking vs. Non-blocking**: 2PC blocks, 3PC avoids blocking but has other costs
2. **Strong vs. Weak consistency**: Strict ACID vs. eventual consistency models
3. **Centralized vs. Decentralized**: Single coordinator vs. peer negotiation
4. **Synchronous vs. Asynchronous**: Blocking coordination vs. event-driven
5. **Optimistic vs. Pessimistic**: Assume success vs. prepare for failure
6. **Exact vs. Eventual**: Immediate consistency vs. convergence over time
7. **Performance vs. Correctness**: Faster execution vs. stronger guarantees
8. **Simplicity vs. Functionality**: Simple protocols vs. feature-rich protocols

## Real World Usage

1. **Financial systems**:
   - Bank transfers between accounts (possibly at different banks)
   - Stock trading: buying/selling securities
   - Payment processing: credit card transactions
   - ATM networks: withdrawals and deposits

2. **E-commerce platforms**:
   - Order processing: payment, inventory, shipping coordination
   - Hotel reservations: room booking, payment, confirmation
   - Airline reservations: flight booking, payment, ticket issuance
   - Rental services: vehicle booking, payment, pickup coordination

3. **Enterprise systems**:
   - ERP systems: coordinating finance, inventory, and human resources
   - Supply chain management: order fulfillment across partners
   - Customer relationship management: sales, marketing, service coordination
   - Healthcare systems: patient records, billing, insurance coordination

4. **Microservices architectures**:
   - User registration: profile creation, email verification, welcome email
   - E-commerce: order processing across inventory, payment, notification services
   - Banking: fund transfers across account, ledger, notification services
   - Travel booking: flight, hotel, car rental coordination

5. **Distributed databases**:
   - Cross-shard transactions in horizontally partitioned databases
   - Multi-region transactions in globally distributed databases
   - Schema changes that affect multiple nodes
   - Backup and restore operations spanning multiple nodes

6. **Cloud platforms**:
   - AWS DynamoDB transactions across multiple items
   - Google Cloud Spanner external consistency
   - Azure Cosmos DB multi-master transactions
   - MongoDB multi-document transactions

7. **Blockchain and distributed ledgers**:
   - Atomic swaps between different cryptocurrencies
   - Multi-signature transactions requiring multiple approvals
   - Smart contract execution spanning multiple accounts
   - Cross-chain transactions between different blockchains

8. **Telecommunications systems**:
   - Call routing: signaling, resource allocation, connection establishment
   - Mobile number portability: coordinating between carriers
   - Roaming agreements: billing and service coordination
   - Emergency services: location tracking and response coordination

## Interview Perspective

### Common Interview Questions

1. What are the ACID properties and how do they apply to distributed transactions?
2. How does the two-phase commit (2PC) protocol work?
3. What is the blocking problem in 2PC and how does 3PC address it?
4. What are the different phases in the three-phase commit (3PC) protocol?
5. How does the Paxos Commit protocol work?
6. What is the Saga pattern and when is it used?
7. What are the advantages and disadvantages of distributed transactions?
8. How do you handle failures in distributed transaction protocols?
9. What is an in-doubt transaction and how is it resolved?
10. How do you choose the right transaction model for an application?

### Common Misconceptions

1. Distributed transactions are always necessary for correct distributed systems
2. Two-phase commit is the only way to achieve atomicity in distributed systems
3. Three-phase commit eliminates all problems associated with 2PC
4. Distributed transactions provide the same guarantees as local transactions
5. The Saga pattern provides ACID guarantees
6. All distributed systems should use strong consistency for transactions
7. Distributed transactions work the same way regardless of underlying technology
8. Coordinator failure in 2PC always requires manual intervention

## Summary

Distributed transactions are essential for maintaining consistency and correctness in distributed systems where operations span multiple nodes. The two-phase commit protocol provides a foundational approach to atomic commitment, though it suffers from the blocking problem. Three-phase commit and Paxos-based approaches address some limitations, while the Saga pattern offers an alternative for long-running transactions. Understanding the characteristics, advantages, disadvantages, and failure modes of different distributed transaction approaches is crucial for designing distributed systems that meet application requirements for consistency, availability, and performance. Real-world systems often use multiple transaction models, applying stronger consistency where needed and more flexible models where performance or scalability is more critical.