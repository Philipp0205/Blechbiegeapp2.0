[[SD - 09 - Event-Drive-Architecture-with-Apache-Kafka-Handout.pdf]]

# What is Event-Driven Architecture

## Event Notification 
- Sender and receiver are decoupled 
- One can function without the other 

- But no overall info about the system 

## Event-carried State Transfer
- Reduced load on supplier 
- Replicated Data

## Event Sourcing
- CRUD based systems forget history 
- Instead: Create event log with information that changed 
	- -> Immutable event log 
- Replicate current state from event log 
	- -> Event sourced system 

Pros 
- Audit, Debugging, Historic State, Alternative State 

## CQRS
Command Query Responsibility Segregation

# Apache Kafka
 - Very efficient pub/sub message broker and 
 - fast key/value data store 
 - Good scalability by partitioning of topics

## How does it work
- Stores messages in topics in an immutable sequence 
- Topics can be partitioned for scalability 
- Producer and Consumer can write to many partitions 

- Partitions can be replicated on different nodes 
- Message processing can be parallelized by multiple consumer instances forming a group