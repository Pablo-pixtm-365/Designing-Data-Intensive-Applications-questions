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
