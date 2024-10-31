# The System Design Primer

Summaries of various system design topics, including pros and cons. Everything is a trade-off.

Scalability:
horizontal scaling
load balancing & caching
shared session state
RAID
shared storage tech
database replication
load balancing tech
session affinity
in-memory caching
data replication – active:passive
partitioning
data center redundancy
security

Clones - requires management of deploy so there are no outdated code running

2 types of cache:

1) Cached Database Queries - Whenever you do a query to your database, you store the result dataset in cache.
2) Let your class assemble a dataset from your database and then store the complete instance of the class or the
   assembled dataset in the cache.

Redis(more complex data, persistent cache) vs Memcached(raw speed)

2 types of asynchronism:

1) Do heavy work in advance. Best for static, predicted data
2) Not blocking the user, just notifying that work is done later. Best for custom data. RabbitMQ is an open-source
   message broker often used for communication between microservices in the cloud.

Performance vs scalability

A service is **scalable** if it results in increased **performance** in a manner proportional to resources added.

If you have a **performance** problem, your system is slow for a single user.
If you have a **scalability** problem, your system is fast for a single user but slow under heavy load.

Latency vs Throughput

Latency is the time to perform some action or to produce some result.

Throughput is the number of such actions or results per unit of time.

Generally, you should aim for maximal throughput with acceptable latency.

Availability vs consistency

In a distributed computer system, you can only support two of the following guarantees:

Consistency - Every read receives the most recent write or an error
Availability - Every request receives a response, without guarantee that it contains the most recent version of the
information
Partition Tolerance - The system continues to operate despite arbitrary partitioning due to network failures
Networks aren't reliable, so you'll need to support partition tolerance. You'll need to make a software tradeoff between
consistency and availability.

CP - consistency and partition tolerance
Waiting for a response from the partitioned node might result in a timeout error. CP is a good choice if your business
needs require atomic reads and writes.

AP - availability and partition tolerance
Responses return the most readily available version of the data available on any node, which might not be the latest.
Writes might take some time to propagate when the partition is resolved.

AP is a good choice if the business needs to allow for eventual consistency or when the system needs to continue working
despite external errors.

