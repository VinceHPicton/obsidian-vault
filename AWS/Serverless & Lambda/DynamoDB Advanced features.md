
**DynamoDB accelerator (DAX)**
- This is caching for DynamoDB and it's a **complimentary** method of caching to [[Elasticache]] - you can use both together
	- Elasticache is more for storing the result of a big computed operation on the DB, DAX is for caching individual objects.
- Gives you **microsecond** latency for the cached data
- 5 Minute TTL by default.

![[DynamoDB Advanced features.png|250]]

**DynamoDB streams**
Allows you to record an ordered steam of the operations that happened to your DynamoDB table, is an alternative to [[8. Kinesis Data Streams]]

DynamoDB streams retain data for 24 hours, while kinesis holds for a year and has a larger number of available consumers
![[DynamoDB Advanced features 1.png]]

**Global tables**
These are active-active two-way replications of your database across regions, you must **enable DynamoDB data steams** in order to use this feature, the reason to use it is to put DB instances closer to users for latency. You can read and write to all copies.


**Time to live (TTL) feature**
This is lets you delete records after a certain time period, you do it by setting an expiry time on a record (ExpTime), a big reason to do this might be to **expire user sessions** requiring them to relogin.

**How to backup DynamoDB**
There are 2 ways to do it, you can use both:

***Continuous backups (PITR):***
- Recover to any point in time in the last 35 days - (PITR - point in time recovery)
- Recovery process creates a new table

***On-demand backups:***
- For long term backups, retained forever until deleted
- No effect on performance of DB
- Cna be configured in the AWS backup service
- Also creates a new table on recovery.

**S3 integration**
Export DB to S3 (must enable PITR)
- Possible uses: data analysis, retain snapshots to audit
- Perform ETL on data before importing back to Dynamo

**Importing/exporting from S3**
- CSV DynamoDB JSON or ION formats
- Doesnt use any write capacity to import.
- Doesn't use any read capacity to export if within the PITR window (35 days)