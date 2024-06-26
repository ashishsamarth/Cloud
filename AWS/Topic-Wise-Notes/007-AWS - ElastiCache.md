AWS - ElastiCache
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Elastic Cache is used to manage in-memory (high performance, Low Latency) databases like Redis or MemCached, similar to what RDS does for Postgres or MySQL. This helps to reduce load off of databases for read intensive workloads. It also helps to make your applications stateless

Since this is a managed service like RDS, AWS takes care of the OS maintenance / patching, optimizations, setup, configuration, monitoring, failure recovery
and backups.

Note: Using ElastiCache involves heavy application code change in your application, depending on how your application reads the data from the database.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    ElastiCache Solution Architecture: Database Cache

                                        ---------------------
    -------------                       |  AWS ElastiCache  |
    |           |       Cache HIT (1)   |                   |
    |           |     <-------------->  |                   |
    |APPLICATION|      Cache MISS (2)   |                   |                   -------
    |           |     ----------------> |                   |                   | AWS | 
    |           |                       |                   | Read From DB(3)   | RDS |
    |           |  <----------------------------------------------------------> |     |
    -------------      Write to Cache(4)|                   |                   -------
                    ---------------->|                   |
                                        ---------------------

Applications queries ElastiCache first, if the data is not available in cache, then the call is made to RDS. Once the data is retrieved, if several instances are asking for the same information, then such information is stored in cache.

This architecture, relieves load on RDS instance.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Special Note: Cache must have an invalidation strategy to make sure only the most current data is used in there.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Once such example is:
        For your application you can maintain the user login session data in to ElastiCache, so that even if the user 
        get connected to another instance, The user will be able to continue the activity without login in again for 
        another instance, since application will be able retrieve the session data from ElastiCache
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Additional Info from another source:
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Elasticache is in-memory caching that can be used in front of any RDS database and can be used in front of 
    a DynamoDB database as well
        a. Elasticache is in-memory cache in the cloud
        b. Improves performance of web applications, allowing you to retrieve information from fast in-memory 
            caches rather than slower disk-based databases
        c. Sits between your application and the database
            E.g. an application that frequently requests specific product information for your best selling products
        d. Takes the load off of your databases
        e. Good if your database is particularly read-heavy and the data is not changing frequently

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Elasticache Benefits and Use Cases

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a. Improves performance for read-heavy workloads. E.g. Social Networking, gaming media sharing, and Q&A Portals
    b. Frequently-accessed data is stored in-memory for low latency access, improving overall performance of the application
    c. Also good for compute-heavy workloads (e.g. recommendation engines)
    d. Can be used to store results of I/O intensive database queries or output of compute-intense calculations

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q01: What is REDIS?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Redis is ‘an open source (BSD licensed), in-memory data structure store, used as a database, cache, and message broker.
Redis is a way to store key-value pairs, in a selection of different data types such as Lists, Sets, and Hashes. Redis keeps this data in memory, meaning that it is extremely fast to return the data when requested. This speed makes it perfect as a cache for your application where you need to request and return data and speed is an important factor

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q02: What is MemCached?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
MemCached is a ‘Free and open source, high-performance, distributed memory object caching system’. Like Redis, Memcached is an open source way to store key value pairs in memory, meaning that data is very quickly retrieved. This makes Memcached another way to return data where speed is a factor. Memcached is also multithreaded, meaning that there may be some performance improvements where your application can utilize multiple cores

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q03: What Is Different About Redis and Memcached?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
There are a number of key differences between Redis and Memcached which need to be mentioned. These differences are very specific around how Redis and Memcached handle the data they are caching, and how they are able to deal with it at scale

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    ElastiCache - REDIS Vs MemCached.

                                REDIS                                                                   MEMCACHED
        a.  Supports Multi-AZ with Auto-Failover                                    a.  Multi-node for partitioning of data (sharding)
        b.  Suports Read Replicas to scale reads and have high availability         b.  No high availability (replication)
        c.  Data Durability using AOF (Append only File) persistence                c.  Non Persistent
        d.  Back-up and Restore Features                                            d.  No Backup and Restore
        e.  Supports different data-types natively                                  e.  Multi-Threaded Architecture

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q04: When to Use Memcached?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Memcached is, by design, very simple to set up and use. If you have an extremely simple application on only a few servers, and only required simple string interpretation for your application, then Memcached may be the correct choice for you. However, even with small workloads, it may be worth the little extra effort to set up Redis, as it has the option for expandability later on.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q05: When to Use Redis?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Redis is a very well rounded, mature product, with active ongoing development. It has a bunch of features and really gives the option for expandability into the future. You should be using Redis when:

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  You need access to a wider set of data structures and stream processing capability.
    b.  The ability to modify and change keys and values in place is required.
    c.  Custom data eviction policies are required (for example, needing to keep keys with a longer Time to Live, even if system is out of memory).
    d.  You need to persist your data to disk for backups and warm restarts
    e.  You need to have high availability or scalability of your application, through the use of replicas and clustering.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q06: Explain different Cache Implementation Strategies?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following are the Cache Implementatoion Strategies, first look at the considerations:
        
        a.  Is it safe to Cache data            :   Data may be out of data, and eventually consitent
        b.  Is Caching effective for that       :   Pattern         : Data is Changing slowly, few keys are frequently used
                                                    Anti Patterns   : Data is Changing rapidly, all large key space frequently needed
        c.  Is Data structured well for caching :   Example         : Key value caching, or caching of aggregation results
    
        Following are the strategies:
        a.  LAZY LOADING / CACHE-ASIDE / LAZY POPULATION : All these terms mean the same

                                                ---------------------
            -------------                       |  AWS ElastiCache  |
            |           |       Cache HIT (1)   |                   |
            |           |     <-------------->  |                   |
            |APPLICATION|      Cache MISS (2)   |                   |                   -------
            |           |     ----------------> |                   |                   | AWS | 
            |           |                       |                   | Read From DB(3)   | RDS |
            |           |  <----------------------------------------------------------> |     |
            -------------      Write to Cache(4)|                   |                   -------
                               ---------------->|                   |
                                                ---------------------

            Pros:
                1.  Only requested data is cached (The cache is not filled with un-used data)
                2.  Node Failures are not fatal (just increased latency to warm the cache)
            
            Cons:
                1.  Cache miss penalty results in 3 round trips (step 2,3,4), accounting to noticable delay
                2.  Stale Data: Data can be updated in the database and outdated in the cache
            
            E.g. Python Code to display this:
            
            def get_user(user_id):
                # Check the Cache
                record = cache.get(user_id)

                if record is None:
                    # Run a db query
                    record = db.query("Select * from users where id=?", user_id)
                    # Populate the cache
                    cache.set(user_id, record)
                    return record
                else:
                    return record
            
            # App Code
            user = get_user(17)
        
        b.  WRITE THROUGH (Add or Update Cache when Database is updated)


                                                ---------------------
            -------------                       |  AWS ElastiCache  |
            |           |       Cache HIT       |                   |
            |           |     <-------------->  |                   |
            |APPLICATION|                       |                   |                   -------
            |           |                       |                   |                   | AWS | 
            |           |                       |                   | Write to DB (1)   | RDS |
            |           |  <----------------------------------------------------------> |     |
            -------------      Write to Cache(2)|                   |                   -------
                               ---------------->|                   |
                                                ---------------------
            
            Pros:
                1.  Data in cache is never stale, reads are very quick
                2.  Write penalty requires two writes (1 and 2)
            
            Cons:
                1.  Missing Data until it is added / updated in the DB. Mitigation is to implement Lazy Loading strategy as well.
                2.  Cache Churn: A lot of the data will never be read

                E.g. Python Code to display this:

                def save_user(user_id, values):

                    # Save to DB
                    record = db.query("update users....where id=?", user_id, values)
                    # push into cache
                    cache.set(user_id, record)
                    return record
                
                # App Code
                user = save_user(17, {"name": "Data Dog"})
            
        c. CACHE EVICTIONS and TIME-to-LIVE(TTL)
            Cache Evictions can occur in three ways.
                1.  You Delete the item explicitly in the cache
                2.  Item is evicted because the memory is full and its not recently used (LRU = Least Recently Used)
                3.  You set an item time-to-live (or TTL)

            TTL are helpful for any kind of data:
                a.  Leaderboards
                b.  Comments
                c.  Activity Streams
            TTL can range from a few seconds to hours or days

            IF too many evictions happen due to memory, you should scale out.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q07: Explain different types of ElastiCache replication?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Their are two types of ElastiCache replication (only for REDIS, since MemCached does not support replication)
        
        a.  Cluster Mode Disabled
            1.  This mode has - Once primary node and upto 5 replicas in a SINGLE SHARD
            2.  Their is asynchronous replication between replica nodes and the primary nodes, so all nodes will e
                ventually have the data.
            3.  The Primary Node is used for read / write.
            4.  The other nodes (replicas) are ONLY for READ.
            5.  This mode provides protection against data loss due to node failure, since data is replicated
            6.  Multi-AZ options is enabled by default for this mode to support Failover
            7.  This mode is helpful to SCALE READ PERFORMANCE.

        b.  Cluster Mode Enabled
            1.  This mode has - One primary node and upto 5 replicas in a MULTI SHARD Arrangement, across each shard
            2.  Data is partitioned across shards (helpful to scale writes)
            3.  Multi-AZ capability

-----------------------------------------------------------------------------------------------------------------------------------------------------------