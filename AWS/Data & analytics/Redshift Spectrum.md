Allows you to query data in S3 using SQL (eg SELECT, AGGREGATE commands) as if it were in your redshift DB, without having to do an ETL to actually load it into redshift first.

This allows you to use a cluster to query S3 data without having to load it into the cluster.
A cluster must be available to start the query, it is then forwarded to thousands of spectrum nodes.
![[Redshift 1.png]]
