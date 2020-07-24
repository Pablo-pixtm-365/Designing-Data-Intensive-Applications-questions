## Designing-Data-Intensive-Applications-questions

#### Chapter 2

1.- How are most applications created?
They are created by superimposing one data model on another.

2.- What was the purpose of the database relation model?
> was to hide that implementation detail behind a cleaner interface.

3.- What was NoSQL originally intended for?
> It was simply intended as a catchy Twitter hashtag for a meeting in open source, distributed, and non-relational databases in 2009.

4.- mentions an advantage of NOSQL databases over SQL:
> Greater scalability in very large data set or higher write performance.

5.- What is polyglot persistence in DBs?
> Both relational and NOSQL databases will continue to be used in conjunction in the future.

6.- How do you tell the disconnect between SQL data models?
> Impedance mismatch. (Desajuste de impedencia).

7.- What type of relationship and union is used routinely in relationships databases?
> Many-to-many relationships and unions are routinely used.




#### Chapter 3 

1.- Is word registration often used to refer to?
> application logs.

2.- What do we need if we want to search the same data in several different ways?
> need several different indexes on different parts of the data.

3.- Why does any kind of index slow down writing?
> because the index also needs to be updated every time data is written.

4.- What type of indexing does the default storage engine use in Riak?
> Hash Indexes.

5.- What does compaction do?
> makes the segments much smaller.

6.- What are the storage engines based on? & How are they known?
> are based on the principle of merging and compacting ordered files, called LSM storage engines.

7.- What is the standard index implementation in almost all relational DBs and many NOSQL?
> B-Trees

8.- What does b-tree indexing do with the DB?
> Divide the database into blocks or fixed-size pages.

9.- What is needed to make a database with tree-B implementation resistant to locks?
> Tree B implementations include an additional data structure on disk: a write-ahead record (WAL, also known as a redo record).


#### Chapter 4

1.- By what another name is the progressive update known?
> Also known as a staged rollout.

2.- Why is forward compatibility more complicated?
> Forward compatibility can be more complicated as it requires older code to ignore additions made by a newer version of the code.

3.- What is serialization or classification?
> Translation of the memory representation into a sequence of bytes.

4.- Mention some disadvantages of using xml and json as standardized encodings?
 + XML cannot distinguish between a number and a string consisting of digits (except when referring to an external schema).
 + JSON distinguishes strings and numbers, but does not distinguish integers and floating-point numbers, and does not specify a precision.
 + JSON and XML do not support binary strings (byte sequences without character encoding).

5.- What is the length of a binary encoding?
> A length of 66 bytes.

6.- In serialization methods like Thrift, when can we add a new field?
> If you give each field a new tag number.

7.- What about changing the datatype of a field?
> There is a risk that values will lose precision or get trunca‐ted

8.- What can we use in Avro to allow a field to be null?
> We must use the union type. For example, union {null, long, string} field;

9.- What acts as documentation and gives you an opportunity to check schema compatibility?
> A schema version database.

10.- Why is backward compatibility in a database important?
> Because this means that a value in the database can be written by a newer version of the code, and later read by an older version of the code that is still running without losing the information if we are careful.


### Chapter 5

1.- What is replication in a few words?
> Replication means keeping a copy of the same data on multiple machines that are connected via a network.

2.- How does leader-based replication work?
> First a replica is defined as leader, this is the one in charge of writing the requests of the clients in their local storage, the other replicas are known as followers.
> second, once the leader did the writing, the leader sends the data change to all the followers, known as replica or flow change. Literal followers follow the leader in making a local copy of his record.
> Third, clients can read data from the leader or any follower but writes can only be done by the leader.

3.- Mention an advantage and disadvantage of synchronous replication
> Advantage:
This ensures that the follower will have an up-to-date copy of the data that is consistent with the leader. If the leader suddenly fails, we can be sure that the data is still available on the follower.

> Disadvantage:
If the synchronous follower doesn’t respond (because it has crashed, there is a network failure, or for any other reason), the write cannot be processed. The leader must block all writes and wait until Synchronous Replica is available again.

4.- What is the name of the process in which a follower becomes a leader?
> Called failover.

5.- When a replica is a good candidate to be a leader?
> It is the replica with the most updated data changes from the previous leader, this in order to lose less information.

6.- According to the book, what is the divided brain?
> Two nodes both believe they are the leader.

7.- Suppose the company where you work asks you to make a replication record of the data, but you do not have much experience on the subject, what implementation of replication records would you use and why?
> Statement-based replication, because it is the simplest case, it is quite compact and there are still DBs that use it by default.

8.- In what situation do you need a consistency of reading?
> When the user sees the data shortly after writing, the new data may not have reached the replica yet, because it was inserted, but it cannot be read because it was not yet loaded into the followers.

9.- Briefly, what does leader-based replication allow?
allows more than one node to accept writes

10.- Does it rarely make sense to use a multi-leader setup within a single data center? true / false and why?
> True, because the benefits rarely outweigh the added complexity.

### Chapter 6

1.- Why although each record belongs to exactly one partition, it can still be stored on several different nodes?
> For fault tolerance.

2.- When a node can store more than one partition?
> When using a leader-follower replication model.

3.- What is a skewed partition?
> When the partition is unfair, so some partitions have more data or queries than others.

4.- What are partition limits for?
> To distribute the data evenly.

5.- What is a consistent hash according to the book?
> It is a way to evenly distribute the load through a caching system across the Internet, such as a content delivery network (CDN).

6.- mentions a use of the concatenated index approach
> Allows an elegant data model for one-to-many relationships, for example on a social networking site, a user can post many updates. Choosing the primary key for updates can efficiently retrieve all updates made by a particular user within a time interval, sorted by time stamp.

7.- Is there a recipe or panacea for skewed workloads today?
> There is no secret formula or something similar, the book mentions a technique that consists of adding a random number to the end of the key, the problem is that there is more work at the time of reading. 

8.- Where are secondary indices common? And what are they useful for?
> Are the foundation of relational databases and are also common in document databases and are useful for data modeling.

9.- Mention one advantage and disadvantage of a global index:
> Advantage: readings can be faster and more efficient.
> Disadvantage: writes are slower and more complicated, because writing to a single document can now affect multiple documents.

10.- According to the book, what is rebalancing?
> The process of moving the load from one node in the cluster to another.

### Chapter 7

1.- According to the book, what is a transaction?
> A transaction is a way for an application to group multiple reads and writes together into one logical unit. 

2.- In a few words, how do we know if a system needs transactions?
> We must understand exactly what security guarantees transactions can provide and what costs are associated with them.

3.- Is it true or false that both relational and non-relational DBs support transactions?
> True

4.- What is the meaning of the acronym ACID?
> Atomicity, Consistency, Insulation and Durability.

5.- In ACID what is atomicity?
> In general terms it means aborting or canceling a transaction due to an error made by the user or by the system itself, which allows the system to pretend that nothing happened.

6.- In ACID, what is consistency?
> It means that the DB is in good condition, that is, that the invariants data must always be true.

7.- What is the only ACID term that references (property) databases? 
> The consistency is a property of the application.

8.- What is the disadvantage of using isolation in the sense of ACID?
> It carries a performance penalty

9.- What is a key feature of transactions?
> Is that it can be safely aborted and reattempted if an error occurs.

