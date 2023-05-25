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