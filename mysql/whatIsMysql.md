### Intro
```The client process sends a piece of text (a MySQL statement) to the server process, which processes it and then sends a piece of text (the processing result) back to the client process. The server program's handling of the query request from the client process generally goes through three parts: connection management, parsing and optimization, and storage engine.```

### Connection management
```The client process can use one of the methods we mentioned earlier, such as TCP/IP, named pipes or shared memory, or Unix domain sockets, to establish a connection with the server process. Whenever a client process connects to the server process, the server process creates a thread to handle the interaction with that client. When the client exits, the server disconnects it, but it does not immediately destroy the thread that interacted with that client. Instead, it caches it, and when a new client connects, it assigns this cached thread to the new client. This way, it achieves the effect of saving expenses by not frequently creating and destroying threads. From this point, we can also see that the MySQL server assigns a thread to each client that connects, but assigning too many threads can seriously affect system performance, so we need to limit the number of clients that can connect to the server at the same time.```

```When the client program initiates a connection, it needs to carry host information, username, and password. The server program will authenticate these pieces of information provided by the client program. If the authentication fails, the server program will refuse the connection. Additionally, if the client program and the server program are not running on the same computer, we can also use a network connection that has SSL (Secure Socket Layer) enabled to ensure the security of data transmission. After the connection is established, the server thread associated with the client will wait for requests sent from the client. The requests received by the MySQL server are just text messages.```
### Parsing and Optimization
#### Query Cache
```The MySQL server is not intelligent enough to recognize the similarities between two queries that differ in any character, such as white space, comments, or case. This results in a cache miss. Additionally, if a query request contains certain system functions, user-defined variables and functions, or some system tables such as tables in the mysql, information_schema, or performance_schema databases, the request will not be cached.```

```MySQL's caching system monitors every table involved in a query. Whenever the structure or data of a table is modified, such as through the use of INSERT, UPDATE, DELETE, TRUNCATE TABLE, ALTER TABLE, DROP TABLE, or DROP DATABASE statements, all cached queries that use that table will become invalid and be removed from the cache.```
#### Syntax Parsing
```This involves stages such as lexical analysis, syntax parsing, and semantic analysis.We shall discuss later.```
#### Query Optimization
```After syntax parsing, the server program obtains necessary information such as the columns to query, which table to query, what the search conditions are, etc. However, having just this information is not enough, as the efficiency of executing MySQL statements may not be very high. MySQL's optimization program will optimize our statements by converting outer joins to inner joins, simplifying expressions, and converting subqueries to joins, and so on. The result of optimization is to generate an execution plan, which indicates which indexes should be used for querying, and what the order of table joins should be. We can use the EXPLAIN statement to view the execution plan of a specific statement.```
### Storage Engine
```The MySQL server encapsulates the storage and retrieval operations of data into a module called a storage engine. We know that a table is composed of rows of records, but this is only a logical concept. How records are physically represented, how data is read from tables, and how data is written to specific physical storage devices are all responsibilities of the storage engine. To implement different functionalities, MySQL provides a variety of storage engines, each managing tables with different storage structures and access algorithms. To facilitate management, functions that do not involve actual data storage, such as connection management, query caching, syntax parsing, and query optimization, are classified as functions of the MySQL server. The function of accessing and storing real data is classified as the function of the storage engine. Various storage engines provide a unified call interface (the storage engine API) to the MySQL server layer above, which contains dozens of low-level functions, such as "read the first content of an index", "read the next content of an index", "insert a record", and so on.```

|Storage Engine | Description |
| ---- | ---- |
|ARCHIVE | Used for data archiving (rows cannot be modified once they are inserted).|
|BLACKHOLE|Discard write operation, and the read operation will return an empty result.
|CSV|When storing data, separate individual data items with a comma.
|FEDERATED| Used for accessing remote tables.
|InnoDB|A transactional storage engine that supports foreign keys.
|MEMORY| Placed in memory.
|MyISAM| The main non-transactional storage engine.
|NDB|For Mysql clusters

#### Set Storage Engines for Tables
***When creating:***

```sql
create table engine_demo_table(
    i int
)engine = MyISAM;
```

***When changing:***

```sql
alter table engine_demo_table engine = InnoDB;
```
