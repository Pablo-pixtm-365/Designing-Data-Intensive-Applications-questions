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
