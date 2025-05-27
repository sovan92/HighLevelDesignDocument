## Kafka topic Details .

When creating a kafka topic , you can create a number of partitions. You may not be able to reduce the number of partitions. 
Think of partition is a linklst and the end where data is stored is called as a offset. 
Across partition the order is ordered.  By default kafka topic stores data permanenely . 
When same key is provided , the event should be present in same partition , otherwise kafka kind of divides it in round robin fashion . 

