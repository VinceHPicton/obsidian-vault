A **serverless** querying service to analyse data stored in S3 using **SQL**.

Supports CSV, JSON, ORC, Avro, Parquet, 5 USD/TB of data scanned


**How to improve performance and cost**
- Use [[Glue]] to convert daya to parquet or ORC and then use **columnar data** for huge perf imrpovement
- **Compress** the data (zip)
- **Partition** data using "folders"
	- Eg: s3://mybucket/flights/year=1999/month=1
- Use **larger files** (over 128MB) makes queries more efficient



**Federated query**
You can also use Athena to query data **anywhere** - relational, non relational, object and custom data sources on AWS or on-prem

You do this by using a data source connector which runs on a lambda to query the target.
You can then store the results of the query back in S3.

![[Amazon Athena.png]]