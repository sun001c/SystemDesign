Examples


Media Streaming - Youtube, PrimeVideo

Non functional - data can be inconsistent - eventual consistency no sql database. 
Video - Encoder. The encoder converts videos into multiple formats and the streaming server sends it to the client. Encoders and transcoders compress videos and transform them into different formats and qualities to support varying numbers of devices according to their screen resolution and bandwidth. - Segments and chunks
Adaptive bitrate streaming is a common technique used to provide a good streaming experience to the user.
Bigtable is a good choice for storing thumbnails because of its high throughput and scalability for storing key-value data. Bigtable is optimal for storing a large number of data items each below 10 MB. Therefore, it is the ideal choice for YouTube’s thumbnails.
Youtube Search
Deployment
Duplication of videos




News Feed - Quora/ Reddit/ Twitter - 










Everytime customer visits the reddit homepage, we need to update the feed with new posts. So we should be doing this on demand and we have to cache top posts. 
Vertical Sharding? 
Push vs Pull Approach ? Hybrid Approach? For generating news feed 
Concurrent writes/reads? 
Sharded Counters
Crawler? 



Social Media - Instagram, TikTok

Feed generation service - Push vs Pull, Lazy loading
Interactions - Sharded counters














Parking Garage








Messaging Apps - Whatsapp, Messenger - go through educative for highlights

HTTP(S) doesn’t keep the connection open for the servers to send frequent data to a client. With HTTP(S) protocol, a client constantly requests updates from the server, commonly called polling, which is resource intensive and causes latency. WebSocket maintains a persistent connection between the client and a server. This protocol transfers data to the client immediately whenever it becomes available. It provides a bidirectional connection used as a common solution to send asynchronous updates from a server to a client. we must use web sockets for connection. Web sockets maintain the connection until the end of session. Whereas HTTP requests terminate connection after the data is sent. Web sockets are also built on TCP and they have an upper limit of 65000 sessions. So, we need to maintain a huge number of server’s.

According to the CAP theorem, the system would provide either consistency or availability in the event of a network partition. In our system of a WhatsApp messenger, the correct ordering of messages is essential. Otherwise, the context of the information communicated between users might change significantly. Therefore, availability in our system can take a hit if the network partition occurs.
Mnesia database
Focus on messaging Queue - Consistency Strict ordering
Group service and Group message handler
Encryption and decryption














Google Docs

Conflicts - Operational Transaction, Conflict free replicated data type - CRDT
Commutativity and Idempotency

Amazon Kindle Payments.


User -> Digital Good. Digital goods we need not worry about inventory
Archive Payments 
We don’t want to store any content. But, just store the financial records. 
More write than read. 
We want consistent data - so RDBS would be the preferred choice. 
Cassandra we will have eventual consistency. Distributed consensus, replication factor
Not lot of caching - we can use LRU 
We need a payment service provider. 
Using Messaging Queue for sending out Notifications. 















Proximity Service - Yelp/ UberEats

QuadTree servers: These are a set of servers that have trees that contain the places in the segments. A QuadTree server finds a list of places based on the given radius and the user’s provided location and returns that list to the user. This component mainly aids the search functionality.

Aggregators: The QuadTrees accumulate all the places and send them to the aggregators. Then, the aggregators aggregate the results and return the search result to the user.






Google Maps - 


Vending Machine









TicketMaster - Hotel Booking Service
Guest account, create a user account
Browse tickets
Payment
notification







ChatGPT
Func Req: Conversations, LLM Model 
Non func - scalable, latency, available, eventual consistency

User client -> load balancer -> LLM model, conservation service, -> cache -> DB




Distributed Key Value Storage MemCache
Distributed hash tables
What is Key and value 
Applications
Requirements - Functional, Non Functional
API design
Consistent Hashing
Replication - 
Vector clocks
Quorum


Messaging Queue

Distributed Cache

Distributed Search



Rate Limiter








Web Crawler

Where do we get these seed URLs from? - There are two possible ways to create or gather seed URLs: We can manually create them. We can scan the IP addresses for the presence of web servers. 

How do we select seed URLs for crawling? There are multiple approaches to selecting seed URLs. Some of them are: Location-based: We can have different seed URLs depending on the location of the crawler. Category-based: Depending on the type of content we need to crawl, we can have various sets of seed URLs. Popularity-based: This is the most popular approach. It combines both the aforementioned approaches. It groups the seed URLs based on hot topics in a specific area.

Why are good quality seed URLs important and what happens if the seed quality is not good? When we model WWW as a graph where URLs link one node to another, our goal is to discover as much of it as possible during the crawl. Using a low-quality seed might limit the discovery to just a fraction of the WWW graph.




Auto-complete

TinyURL
Custom short links 
Encoding - look alike characters, min length of 6 characters, alphanumeric characters, lifetime. 
Short url generator
MongoDB - 1:100 short:redirect ratio
Scale
Metrics and Logging Service







