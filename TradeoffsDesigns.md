# System Design Tradeoffs

## SQL vs NoSQL 

SQL is usually high consistency
NoSQL usually is built with eventual consistency . 
SQL generally has a read replicas. NoSQL out of the box comes with clusters. 
NOSQL Leader election , Consensus algorithm . ,  SQL has a primary and secondary replicas. 
SQL has single source of truth. (PRIMARY)
NOSQL comes with inbuilt sharding , where was SQL will have to create that. 
Usually NoTransaction ACID Support in NOSQL (Cassandra, Dynamo DB, Mongo DB ), In SQL usually there is transaction support. 
