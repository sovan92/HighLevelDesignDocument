# System Design Tradeoffs

## SQL vs NoSQL 

SQL is usually high consistency
NoSQL usually is built with eventual consistency . 
SQL generally has a read replicas. NoSQL out of the box comes with clusters. 
NOSQL Leader election , Consensus algorithm . ,  SQL has a primary and secondary replicas. 
SQL has single source of truth. (PRIMARY)
NOSQL comes with inbuilt sharding , where was SQL will have to create that. 
Usually NoTransaction ACID Support in NOSQL (Cassandra, Dynamo DB, Mongo DB ), In SQL usually there is transaction support. 

## Latency vs accuracy

Database vs Cache . 


## Consistency Vs Availability 

Strong consistency 
Ticket booking 
Event booking. 
Inventory system, we can't seel last item to multiple customers. 
Financial Systems , stock sell should be in order. 

## How does it affect my design 
- Implement distributed transactions.
- Limit to a single node.
- Discuss consensus protocol.
- Accept higher latency
- Example tools
-   PostgresSQL
-   Triad DBMS
-   Spanner

If stroing availability is a concern 
Read replicas . 

- Ticket Master -
- Availability for crud event (searching and viewing event)
- Consistency for booking tickets.(Double booking)

Tinder 
- availability for profile data
- consistency for matching .

Strong consistency - Read after every write is visible. 
Causal Consistency - Related events appear in order 
Read your write consistency - User sees their own updates. 
Eventual Consistency - Updates will propagate eventually . 



