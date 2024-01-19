# Requirements

## Functional
- Consider MVP features and check if these are enough or if they want more?
- Split functional requirements by type of users. Refer Uber Eats
- Data Consistency - Strong or eventual

## Non-Functional
- Scalability
- Availability - 99.999%
- Latency - Viewing 150ms
- Security
  - Authentication & Authorization
  - Request validation
  - Rate Limiting
  - DDOS
- Handle concurrency issues where writing & reading can be performed simultaneously.

## Clarifying Questions
- What kinds of data - text, images, video, audio, thumbnails?
- What clients do we want to support - Web or mobile?
- Do we want to store the data or not for security reasons?
- What’s the primary purpose for this product? How are we defining metrics of success at the end?
- How fresh is the data? Do we want real-time processing?
- How long do we have to store the data? Data retention
- How are the users distributed across the world?
- Social media apps maximum number of friends/followers?
- Messaging apps message body maximum characters?

## Scale - Back of the envelope estimation
- Total Requests - 500M DAU
- Total Data - DAU * amount of data each user posts
- Total Bandwidth (gbps)
- CDN cost per Gb of data streaming - $0.02 (Amazon)

# API Design

- GraphQL vs Rest vs gRPC
- CRUD operations
- API Gateway
  - Advantages
  - Disadvantages

# Network Protocols

- HTTP, HTTPS
- TCP, UDP
- Polling, Long polling, Web sockets

# Domain Name System (DNS)

- What is DNS?
- DNS structure
- UDP protocol
- DNS as a distributed system - scalable, fast, available, eventual consistency.
- DNS as a Load Balancer

# Rate Limiter

- What is a rate limiter
- Advantages
- Functional and non-functional requirements
- Throttling
- Where to place the rate limiter
- Design & Implementation
- Algorithms
- Race conditions - Concurrent write requests

# Load Balancing

- What is a Load Balancer?
- Global vs Local LB
- Advantages
- Algorithms for load balancing?
- Static vs Dynamic?
- Stateful vs Stateless
- Layer 4 vs 7
- Deployment of LB

# API Design

- API stands for Application Programming Interface.
- GraphQL, Queries, Schema, Resolver
- Advantages

# Caching

- What is a cache?
- Cache HIT vs MISS
- Cache write policy?
- Cache Eviction policy?
- Cache invalidation
- Cache client
- Data structure - Hash table, linked list, Bloom filters
- Redis vs Memcached

## Deploying Caches

- Consider deploying Caches on different hosts for scalability and availability.
- Consistent hashing and sharding for cache

## Bloom Filters

- Special data structure used for searching
- Probabilistic algorithm
- Client-side caching, Web server caching, User-specific cache, Distributed cache, Object storage

# CDN

- What is CDN
- Advantages
- Design CDN - APIs
- Push vs Pull
- Compression - Edge Side Includes Markup language
- Finding nearest CDN
- Public vs Private

# Messaging Queue

- What is a messaging queue
- Advantages
- Design - APIs
- Ordering of messages - Strict, best effort
- Concurrency?

# PubSub Model

- What is PubSub model
- Advantages
- Applications
- API

# Monitoring

- Why monitoring
- Central monitoring service - push vs pull
- Client-side vs server-side
- Time series database
- Metrics in blob storage
- Sequencing of events

# Sharded Counters

- Counter is basically that keeps track of something likes, dislikes, views count etc
- Heavy hitters problem
- Top K frequent problem
- Shard the counters
- Design shard counters API
- Redis cache, Cassandra database

# Apache Kafka

- Kafka single point of failure?

# Spark Streaming

- Apache Flink

# Evaluation

- Consistency
- Availability
- Performance
- Scalability
- Security
- SQL - ACID properties

# Synchronous replication

- Cache write through
- Messenger Queue strict ordering

# Consensus algorithms

- Quorum based approach - Split brain

# Evaluation

- Frequent backups to object storage
- Caching
- Database replication within data center or across data centers
- Messenger Queue - Decoupling
- Monitoring service
- Heartbeat Protocol - LB
- TCP and UDP fast network calls
- Consistent Hashing - log n
- Caching - Hash tables constant time complexity for get and put, Doubly linked list constant time complexity for cache eviction. CDN, IXP, ISP
- DB - Indexing, Optimizing queries, Sharding
- Increase the number of message queues, do best effort ordering for the messenger queue.
- Using an appropriate programming language - C for encryption and Python elsewhere
- Async Processing, Autoscaling
- LB - Layer 4
- Load Balancer - we can add more number of servers - Consistent Hashing
- No SQL database - horizontal scaling, Replication, Sharding
- CDN
- Rate limiter - dynamic throttling
- HTTPS protocol
- User authentication and authorization mechanisms - strong password requirements, account lockouts after a certain number of failed login attempts, and two-factor authentication (2FA) for added security.
- Role-based access control (RBAC) to ensure that users can only access the data and features relevant to their role.
- Implement Secure Sockets Layer (SSL) encryption for all transactions to protect sensitive information during transmission.
- Principle of least privilege, granting users only the permissions they need to perform their tasks.
- Availability: System is always available for read and write requests. Partition tolerance means the system continues to work despite message loss or partial failure.
- Handling temporary failures - Quorum
- Handling permanent failures - Merkle Tree
- Data Consistency: Every read request should give up-to-date value. Vertical scaling has consistent data but Horizontal scaling will not have consistent data.
- Strong Consistency
- Eventual consistency
- We have to block read requests from s2 and s3 until the replication is done
- We don’t block read requests from s2 and s3.
- Slow performance and availability
- You see stale data
- Trade-offs - CAP theorem states that a distributed system can deliver only two of the three desired characteristics Consistency, Availability, and Partition tolerance (CAP).
- According to the CAP theorem, the system would provide either consistency or availability in the event of a network partition.
- Bottle-neck
- Potential significant bottleneck in our ticket booking service could be the database, particularly during peak times when many users are trying to book tickets for popular events.
- This could lead to high contention for ticket resources and potentially slow down the system, affecting the user experience. Read/write speeds slow down - Indexing, optimize queries, Sharding
- Other potential bottlenecks such as network latency or service failures can also be addressed.
- Network latency can be reduced by implementing a Content Delivery Network (CDN) to serve static content closer to the user's location.
- Caching at IXP, ISP.
- Add monitoring systems with logging metrics, live dashboards alerts and thresholds
- Geo distribution - Multiple data centers across the world.
- Disaster Recovery - The first and foremost approach of handling a disaster is frequent backups.
- The frequency of backups depends on the size of the data. Daily backups are suitable for our design because we can backup individual data stores and shards without any hassle.
- Of course, backups will be stored at remote destinations because natural disasters can wipe out the entire facility at a location.
- Concurrency, No double bookings - Latest timestamp - Synchronized clocks, Locking mechanism, get-then-set, set-then-get, sharded counters, CRDT SQL ACID - Transaction Isolation Level Serializable - dirty reads, phantom reads, non repeatable reads.
- Serialize and deserialize requests.
- Deadlocks
- Fault Tolerance, Single Point of Failure - Master Slave architecture, Load balancer Hot partition key / Celebrity Multiple sharding keys Data redistribution: Balancing the workload by redistributing data across partitions. Consistent Hashing.
- Analyzing and optimizing queries that contribute to the hot partition problem.
- This can involve query rewriting, indexing, or restructuring the schema to reduce the concentration of access on specific partitions.
- Adding more computational resources or nodes to handle the increased workload on the hot partition.
- Scaling horizontally by adding more nodes can help distribute the load more evenly.
- How unique Id’s are generated
- Partition Tolerance - CAP Feedback
- Check in with the interviewer often if this is what you are looking for? Or focus on some more areas
- Start the HLD with how you would design for 10 people and then scale it
- Anticipate risk and mitigate them.
- Must ask clarifying questions
- Concurrency (i.e. threads, deadlock, starvation, consistency, coherence)
- Common abstractions (i.e. OS, file systems, databases)
- Storage (i.e. memory hierarchy, compression) https://www.geeksforgeeks.org/memory-hierarchy-design-and-its-characteristics/
- Networking (i.e. IPC, TCP/IP, Little's Law)
- Real-world performance (i.e. RAM, disk, SSD, different network technologies)
- Availability and Reliability (i.e. the CAP theorem, failure recovery, ACID properties) - cold site, hot site, backups. Atomicity, isolation, consistency, durability
- Zookeeper
- Little’s law - Number of stationery items in a queue is equal to the rate at which items enter the system multiplied by the average time spent in the queue
