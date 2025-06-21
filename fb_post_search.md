# FB Post Search
You cannot use ElasticSearch, Postgres Full-Text  other other off-the-shelf search functionality. 

## Functional Requirements

1. Users should search by keyword.

- Filters ? No. Let's do keywords .
- Sort ? likes and time .
- Fuzzy sort ? No .
- Personalization . Do you want personalized result .  No .

## Non Functional Requirements 
Searching is a hard problem . 
Low latency reads and reads on FB posts. - 500 ms 
30 ms - framerate in movie . 
if it's 5 sec systems our users are going to lose interest . 
High Throughput - 
High avilable or eventually consistent . within 1 min .
- What does it mean , Your search system should show your new post within a minute . 
- High recall - You should have a good number of posts in your seach

Users  1B DAU . 

- Writes

- Post : Post 1B /100K  = 10^4 post/sec
- likes  : 10 B Likes / 100K = 10^5 likes / secs


- Reads
- Searches: 1B/100K secs per day =  10K searches/sec

Sotrage 

1B * 365*10 years = 3.6T 
Storage : 3.6 T * 1kb = 3.6pb 

## Core Entities

- User
- Likes
- Posts

## APIs or INterfaces

POST /posts
text : 100K

PUT /post/{id}/likes

GET /search?query={keywords}&sort={like,time}



## Dataflow 

## High level design 

## Deep dives. 

- Identify those things that are critical bottlenecks .

- Low latency and high throughput . We have lot of people banging up our search index. And when people search it , it should provide same result so How do I cache it .
- A what's the time to live (TTL) or eviction policy of the cache. Each search service has it's own cache . Then distribute the CACHE using a CDN edge node -> (Akamai), which is globally distributed. 
- Burst of likes and serves . (1m) Kafka topic - For post which are of higher value , we can use a separate kafka topic .
- Reread from the offset , fault tolerance high through put .
- Like count changes 10 times the post creations .
- Lot of like count changes don't impact the user.
-     1M   abc
-     10   def
-      1   ghi
-      0   jkl
-  Batch the like event , with out of store event like Flink . The batching
-  Redis is 100K TPS for a single NOde.  (Redis cluster, keys are separated that's your paritioning or sharding)


