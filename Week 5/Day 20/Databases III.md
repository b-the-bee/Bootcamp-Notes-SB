#databases #data-engineering #data-science 

## Relationships between tables

### One-to-one
Imagine we have a table of students and another table of their contact information
![[Pasted image 20240604093336.png]]
### One to Many
One teacher can teach many classes
![[Pasted image 20240604093357.png]]
### Many to Many
Many students can take many courses
![[Pasted image 20240604093419.png]]

## Theory

### ACID
Acid refers to a standard set of properties that **guarantee** database transactions are processed reliably.

More importantly, it is concerned with how a database **recovers** from any failure during a transaction.

ACID-compliant databases ensure that a database remains accurate and consistent.

### What is a transaction?
A unit of work that is treated as a whole. It either has to happen in full or not at all.
Examples: Imagine transferring money from one bank to another. This requries multiple steps:
1. Withdraw from the source account
2. Deposit it ot the destination account
The operation has to succeed in full. Stopping halfway could mean money is lost.

## ACID Acronyms

### Atomicity
Guarantees that all of the transaction succeeds, or none of it does.

An atomic system must guarantee atomicity in ever situation, including power failures, errors and crashes.

### Consistency
Guarantees that all data stays consistent, as in, the data will be valid according to all of the rules defined on the database.

A transaction should only bring the database from one **valid** state to another

### Isolation
![[Pasted image 20240604094052.png]]

### Durability
Once a transaction is committed, it will remain in the system. even if there's a system crash.
If we tell a user that a transaction has succeeded, it must be factual/ This normally means that completed transactions are recorded to long-term memory like a hard drive.

## CAP
A theorem that states it is impossible for a distributed data store to simultaneously provide more than two out of the following three guarantees:

**Consistency**: Every read receives the most recent write or an error
**Availability**: Every request receives a (non-error) response, without the guarantee that it contains the most recent write
**Partition Tolerance**: The system continues to operate despite an arbitrary number of messages being dropped (or delayed) by the network between nodes

No distributed system is safe from network failures, so partition tolerance needs to be tolerated.
We're left with deciding consistency over availability.

![[Pasted image 20240604094932.png]]

![[Pasted image 20240604094941.png]]

## NoSQL
- Refers to any non-relational DB
- Came about in the late 2000s as cost of storage vary dramatically

- As it decreased, it allowed us to store way more data, which could be structured or unstructed
- Cloud computing has driven NoSQL for its ability to distributed data across multiple servers and regions around the world

### Document DB - A NoSQL Database type
![[Pasted image 20240604095245.png]]


### Key-Value DB - A NoSQL Database type
- Each item contains a key and values
- A value can only be retrieved by referencing its key

- Great for storing large amounts of data but don't need to perform complex queries to retrieve it
- Redis and DynamoDB are popular choices

### Wide -Column Store - A NoSQL Database type
- Stores data in tables, rows and dynamic columns
- Provide a lot of flexibility over relational DBs because each row is not required to have the same columns

- Great for when you need to store large amounts of data and you can predict what your query patterns will be
- Cassandra and HBase are popular choices

### Graph DB - A NoSQL Database type
- Stores data in nodes and edges
- Nodes store information about people, places etc
- Edges contain information about the relationships between nodes

- Great for when you need to traverse relationships to look for patterns like social networks and fraud detection
- Example: Twitter followers or LinkedIn connections
- Neo4j and JanusGraph are popular choices

### So why do we need them?

Dynamic schema - no set structure

Auto-sharding - distribution of the data across servers

Auto replication - allows for high availability

The move to smaller distributed services means not relying on one central DB

Easily scalable - more servers means more replication and load balancing

### They're not the silver bullet

- Sacrificing strong guarantees (which we will see next slide)
- Transactions aren't always supported
- You can end up stuck in the "relational" way of thinking when using them