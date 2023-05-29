# mongodb_interview_preparation

## Theorical Questions Section

### Theorical Question 1

Do you know what is mongo Atlas ?

<details><summary><b>Answer</b></summary>

MongoDB Atlas is an integrated suite of data services centered around a cloud database designed to accelerate and simplify how you build with data.

Run anywhere in the world with Atlas. Deploy a database in over 90 regions on AWS, Azure, and Google Cloud - and expand to be global, multi-region, or multi-cloud when you need it. 

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/atlas/database
</details>

### Theorical Question 2

Do you know what Long-Running Snapshot Queries are ?

<details><summary><b>Answer</b></summary>

Snapshot queries allow you to read data as it appeared at a single point in time in the recent past.

Starting in MongoDB 5.0, you can use read concern "snapshot" to query data on secondary nodes. This feature increases the versatility and resilience of your application's reads. You do not need to create a static copy of your data, move it out into a separate system, and manually isolate these long-running queries from interfering with your operational workload. Instead, you can perform long-running queries against a live, transactional database while reading from a consistent state of the data.

Using read concern "snapshot" on secondary nodes does not impact your application's write workload. Only application reads benefit from long-running queries being isolated to secondaries.

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/long-running-queries/
</details>

### Theorical Question 3

when would we use ordered list of operations vs unordered list of operations ?

<details><summary><b>Answer</b></summary>

With an ordered list of operations, MongoDB executes the operations serially. If an error occurs during the processing of one of the write operations, MongoDB will return without processing any remaining write operations in the list. See ordered Bulk Write

With an unordered list of operations, MongoDB can execute the operations in parallel, but this behavior is not guaranteed. If an error occurs during the processing of one of the write operations, MongoDB will continue to process remaining write operations in the list. See Unordered Bulk Write Example.

Executing an ordered list of operations on a sharded collection will generally be slower than executing an unordered list since with an ordered list, each operation must wait for the previous operation to finish.

By default, bulkWrite() performs ordered operations. To specify unordered write operations, set ordered : false in the options document.

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/bulk-write-operations/
</details>

### Theorical Question 4

what is Avoid Monotonic Throttling and how could you avoid it ?

<details><summary><b>Answer</b></summary>

If your shard key increases monotonically during an insert, then all inserted data goes to the last chunk in the collection, which will always end up on a single shard. Therefore, the insert capacity of the cluster will never exceed the insert capacity of that single shard.

If your insert volume is larger than what a single shard can process, and if you cannot avoid a monotonically increasing shard key, then consider the following modifications to your application:

Reverse the binary bits of the shard key. This preserves the information and avoids correlating insertion order with increasing sequence of values.

Swap the first and last 16-bit words to "shuffle" the inserts.

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/bulk-write-operations/
</details>

### Theorical Question 5

Do you know what this query is doing ?

db.inventory.find( { "size.h": { $lt: 15 } } )


<details><summary><b>Answer</b></summary>

In the collection inventory, inside of the size json, it is looking for the values of the key h where the value is less than 15

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/query-embedded-documents/#specify-match-using-query-operator
</details>

### Theorical Question 6

Do you know what these queries are doing ?

db.inventory.find( { tags: ["red", "blank"] } )

db.inventory.find( { tags: { $all: ["red", "blank"] } } )


<details><summary><b>Answer</b></summary>

![Image](img/matchArrayMongoDB.png "matchArrayMongoDB")

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/query-embedded-documents/#specify-match-using-query-operator
</details>

### Theorical Question 7

How would you query an array of multiple embedded documents ?


<details><summary><b>Answer</b></summary>

https://www.mongodb.com/docs/manual/tutorial/query-array-of-documents/

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/query-array-of-documents/
</details>

### Theorical Question 8

How would you execute the equivalent of this in mongoDB ?

SELECT _id, item, status from inventory WHERE status = "A"

<details><summary><b>Answer</b></summary>

https://www.mongodb.com/docs/manual/tutorial/project-fields-from-query-results/

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/project-fields-from-query-results/
</details>

### Theorical Question 9

How to enable Retryable Writes

<details><summary><b>Answer</b></summary>

https://www.mongodb.com/docs/manual/core/retryable-writes/

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/retryable-writes/
</details>

### Theorical Question 10

How would you find the closest neighbour in mongoDB

<details><summary><b>Answer</b></summary>

https://www.mongodb.com/docs/manual/tutorial/geospatial-tutorial/

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/geospatial-tutorial/
</details>

### Theorical Question 11

How can you adjust the level of consistency and availability guarantees as appropriate, such as waiting for stronger consistency guarantees, or loosening consistency requirements to provide higher availability

<details><summary><b>Answer</b></summary>

https://www.mongodb.com/docs/manual/reference/read-concern/

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/reference/read-concern/
</details>

### Theorical Question 12

What types of write concerns do you know ?

<details><summary><b>Answer</b></summary>

https://www.mongodb.com/docs/manual/reference/read-concern-local/

https://www.mongodb.com/docs/manual/reference/read-concern-available/

https://www.mongodb.com/docs/manual/reference/read-concern-majority/

https://www.mongodb.com/docs/manual/reference/read-concern-linearizable/

https://www.mongodb.com/docs/manual/reference/read-concern-snapshot/

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/reference/read-concern-local/

https://www.mongodb.com/docs/manual/reference/read-concern-available/

https://www.mongodb.com/docs/manual/reference/read-concern-majority/

https://www.mongodb.com/docs/manual/reference/read-concern-linearizable/

https://www.mongodb.com/docs/manual/reference/read-concern-snapshot/
</details>

### Theorical Question 13

How do you execute the explain command in mongoDB ?

what information does it provide ?

what is COLLSCAN and a IXSCAN

<details><summary><b>Answer</b></summary>

https://www.mongodb.com/docs/manual/tutorial/analyze-query-plan/

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/analyze-query-plan/
</details>

### Theorical Question 14

Do you know what is the database profiler

<details><summary><b>Answer</b></summary>

This is a way of finding slow queries, but the problem is that it has an effect on performance so it is off by deafult

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/analyze-query-plan/
</details>

### Theorical Question 15

Do you know what hint is for

<details><summary><b>Answer</b></summary>

In most cases the query optimizer selects the optimal index for a specific operation; however, you can force MongoDB to use a specific index using the hint() method. Use hint() to support performance testing, or on some queries where you must select a field or field included in several indexes.

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/optimize-query-performance-with-indexes-and-projections/
</details>

### Theorical Question 16

Do you know what hint is for

<details><summary><b>Answer</b></summary>

In most cases the query optimizer selects the optimal index for a specific operation; however, you can force MongoDB to use a specific index using the hint() method. Use hint() to support performance testing, or on some queries where you must select a field or field included in several indexes.

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/optimize-query-performance-with-indexes-and-projections/
</details>

### Theorical Question 17

Hardware configuration got making writes perform better ?

<details><summary><b>Answer</b></summary>

Solid state drives (SSDs) can outperform spinning hard disks (HDDs) by 100 times or more for random workloads.

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/optimize-query-performance-with-indexes-and-projections/
</details>

### Theorical Question 18

Do you know what is journaling ?

<details><summary><b>Answer</b></summary>

To provide durability in the event of a crash, MongoDB uses write ahead logging to an on-disk journal. MongoDB writes the in-memory changes first to the on-disk journal files. If MongoDB should terminate or encounter an error before committing the changes to the data files, MongoDB can use the journal files to apply the write operation to the data files.

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/optimize-query-performance-with-indexes-and-projections/
</details>

### Theorical Question 19

what is Slot-Based Query  when does mongoDB use it and how do you know if it been used ?

<details><summary><b>Answer</b></summary>

https://www.mongodb.com/docs/manual/core/aggregation-pipeline-optimization/#sbe-title-pipeline-optimizations

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/aggregation-pipeline-optimization/#sbe-title-pipeline-optimizations
</details>

### Theorical Question 20

Do you know what is a On-Demand Materialized Views ?

<details><summary><b>Answer</b></summary>

https://www.mongodb.com/docs/manual/core/materialized-views/

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/materialized-views/
</details>

### Theorical Question 21

what is a capped collection and when should you use it ?

<details><summary><b>Answer</b></summary>

Capped collections are fixed-size collections that support high-throughput operations that insert and retrieve documents based on insertion order. Capped collections work in a way similar to circular buffers: once a collection fills its allocated space, it makes room for new documents by overwriting the oldest documents in the collection.

if your application only uses recently inserted documents, consider using Capped Collections. 

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/data-modeling-introduction/

https://www.mongodb.com/docs/manual/core/capped-collections/
</details>

### Theorical Question 22

what is schema validation in mongoDB ?

<details><summary><b>Answer</b></summary>

MongoDB uses a flexible schema model, which means that documents in a collection do not need to have the same fields or data types by default. Once you've established an application schema, you can use schema validation to ensure there are no unintended schema changes or improper data types.

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/data-modeling-introduction/

https://www.mongodb.com/docs/manual/core/capped-collections/
</details>

### Theorical Question 23

how would you join values in mongoDB ?

<details><summary><b>Answer</b></summary>

$lookup (Available starting in MongoDB 3.2)

$graphLookup (Available starting in MongoDB 3.4)

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/data-modeling-introduction/

https://www.mongodb.com/docs/manual/core/capped-collections/
</details>

### Theorical Question 24

What is sharding in mongoDB ?

<details><summary><b>Answer</b></summary>

MongoDB uses sharding to provide horizontal scaling. These clusters support deployments with large data sets and high-throughput operations. Sharding allows users to partition a collection within a database to distribute the collection's documents across a number of mongod instances or shards.

To distribute data and application traffic in a sharded collection, MongoDB uses the shard key. Selecting the proper shard key has significant implications for performance, and can enable or prevent query isolation and increased write capacity

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/data-model-operations/
</details>

### Theorical Question 25

What is rolling up in mongoDB ?

<details><summary><b>Answer</b></summary>

You should consider embedding for performance reasons if you have a collection with a large number of small documents. If you can group these small documents by some logical relationship and you frequently retrieve the documents by this grouping, you might consider "rolling-up" the small documents into larger documents that contain an array of embedded documents.

"Rolling up" these small documents into logical groupings means that queries to retrieve a group of documents involve sequential reads and fewer random disk accesses. Additionally, "rolling up" documents and moving common fields to the larger document benefit the index on these fields. There would be fewer copies of the common fields and there would be fewer associated key entries in the corresponding index. See Indexes for more information on indexes.

However, if you often only need to retrieve a subset of the documents within the group, then "rolling-up" the documents may not provide better performance. Furthermore, if small, separate documents represent the natural model for the data, you should maintain that model.

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/data-model-operations/
</details>

### Theorical Question 26

What is a compound index ?

<details><summary><b>Answer</b></summary>

MongoDB supports compound indexes, where a single index structure holds references to multiple fields

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/index-compound/
</details>

### Theorical Question 27

what are hashed indexes useful for in monngoDB ?

<details><summary><b>Answer</b></summary>

Hashed indexes support sharding using hashed shard keys. Hashed based sharding uses a hashed index of a field as the shard key to partition data across your sharded cluster.

Using a hashed shard key to shard a collection results in a more even distribution of data.

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/index-hashed/
</details>

### Theorical Question 28

Do you know what the ESR rule is in monngoDB ?

<details><summary><b>Answer</b></summary>

In compound indexes, first it use the exact match, than it sort values and finally it use the range filter, see an example in the source

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/equality-sort-range-rule/
</details>

### Theorical Question 29

Do you know what network hardening is ?

<details><summary><b>Answer</b></summary>

To reduce the risk exposure of the entire MongoDB system, ensure that only trusted hosts have access to MongoDB.

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/security-hardening/
</details>

### Theorical Question 30

Do you know what redact is for in mongoDB ?

<details><summary><b>Answer</b></summary>

The $redact aggregation pipeline operator in MongoDB is used to redact or hide sensitive data from documents. It can be used to redact fields at the current document level, including embedded documents. To include embedded documents and embedded documents within arrays, apply the $cond expression to the embedded documents to determine access for these embedded documents.

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/implement-field-level-redaction/
</details>

### Theorical Question 31

Do you understand why we need replication in mongoDB ?

<details><summary><b>Answer</b></summary>

The $redact aggregation pipeline operator in MongoDB is used to redact or hide sensitive data from documents. It can be used to redact fields at the current document level, including embedded documents. To include embedded documents and embedded documents within arrays, apply the $cond expression to the embedded documents to determine access for these embedded documents.

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/implement-field-level-redaction/
</details>

### Theorical Question 32

Do you understand what mirrored reads are in mongoDB ?

<details><summary><b>Answer</b></summary>

Mirrored reads reduce the impact of primary elections following an outage or planned maintenance. After a failover in a replica set, the secondary that takes over as the new primary updates its cache as new queries come in. While the cache is warming up performance can be impacted.

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/replication/#mirrored-reads
</details>

### Theorical Question 33

Who  is the only member in the replica set that receives write operations in mongoDB ?

<details><summary><b>Answer</b></summary>

Primary

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/replica-set-members/
</details>

### Theorical Question 34

Do you know what read preferences is in mongoDB ?

<details><summary><b>Answer</b></summary>

By default, an application directs its read operations to the primary member in a replica set (i.e. read preference mode "primary"). But, clients can specify a read preference to send read operations to secondaries.

Read preference consists of the  read preference mode
 and optionally, a tag set list, the maxStalenessSeconds option, and the hedged read option. 

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/read-preference/
</details>

### Theorical Question 35

What is a Priority 0 Replica Set Members in mongoDB ?

<details><summary><b>Answer</b></summary>

A priority 0 member is a member that cannot become primary and cannot trigger elections. Priority 0 members can acknowledge write operations issued with write concern of w : <number>. For "majority" write concern, the priority 0 member must also be a voting member (i.e. members[n].votes is greater than 0) to acknowledge the write. 

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/core/replica-set-priority-0-member/
</details>

### Theorical Question 36

How do you use ip binding when deploying a replica in mongodb ?

<details><summary><b>Answer</b></summary>

Use the --bind_ip option to ensure that MongoDB listens for connections from applications on configured addresses.

</details>

<details><summary><b>Source</b></summary>
https://www.mongodb.com/docs/manual/tutorial/deploy-replica-set/#ip-binding
</details>