Managed relation database service.

You must remember supported DB engines:
- Postgres
- MySQL & MariaDB
- Oracle
- IBM DB2
- Microsoft SQL server
- AWS Aurora

Because it's a managed service you get a lot of features:
- Continuous backups and point in time restores
- Monitoring dashboards
- Read replicas to improve performance
- & many more
- But you **cannot** SSH into the DB server

**Key exam feature: auto scaling with RDS**

RDS can automatically increase its capacity, up to your defined maximum, if:
- Less than 10% of current capacity remains, and has done for 5 minutes
- It has not increased capacity in the last 6 hours

This is supported for **all** DB engines (listed above)