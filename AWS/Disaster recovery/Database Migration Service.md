DMS allows you to migrate your database, and can even allow you to change your DB engine using SCT (schema conversion tool) - meaning going from MySQL to Postgres for eg.
It's primarily designed for one-time migrations, but can be used to continuously update a backup

You can go from pretty much any source incl. on-prem to any of the DB services on AWS.

You need to run an EC2 instance for the DMS to work on, or it can be done serverlessly, but serverless doesnt support ALL Db engines

**The SCT**
You do not need this if you are not changing your DB engine
- Convert an OLTP DB to a different kind
- Or OLAP - eg from Oracle to Redshift

**Continuous Replication**
You can run an EC2 instance to continuously backup an on-prem DB using Change Data Capture (CDC, even continuously to a different engine, you just have to run the SCT tool on the target DB first.

**Multi-AZ**
DMS will maintain a separate 2nd replica of the data