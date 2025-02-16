Redshift is a **columnar database** service (they call it data warehouse) based on PostgreSQL, optimized for [[OLAP]] workloads, whereas Postgres is row-based and suited for OLTP - [[OLAP]] for explanation.

- It has **columnar** based storage.
- Uses a SQL interface for performing queries

Redshift is formed of **clusters**, and can be in either **provisioned or serverless** mode, clusters have a **leader** node and many **compute** nodes.
- Leader nodes plan queries and aggregate the results
- Compute nodes perform queries and send back results.
![[AWS/Data & analytics/Images/Redshift.png|350]]

**Snapshots & disaster recovery**

- Redshift has **multi-AZ mode** for some clusters
- Snapshots are point in time backups of a cluster stoed in S3 and are incremental - only saving what has changed.
- You can restore a snapshot to a new cluster
- Snapshots can be automated with configurable retention: every 8 hours or every 5 GB, or on a schedule
- Manual snapshots are retained forever
- **You can also config a redshift cluster to copy snapshots to another AWS region**

**Loading data into redshift**
Important to note that larger inserts are **much more efficient**

Three examples of ways into insert data:
- S3 - via internet or VPC
- EC2 with JDBC driver
- [[9. Data Firehose]]
![[Redshift2.png]]
