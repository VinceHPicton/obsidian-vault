This is only needed for these 2 options: MySQL and Postgres.

**MySQL**
From within AWS
- Create a snapshot of RDS DB and restore it to Aurora
- Create an **aurora** read replica of your RDS DB, then when there is no replication lag promote it to its own DB

From on-prem
- From on-prem: Use **Percona XtraBackup to S3** and restore to aurora
- From on-prem: Use `mysqldump` to aurora

For both
- Use DMS if both are active

**Postgres**
From within AWS - SAME AS MYSQL
- Create a snapshot of RDS DB and restore it to Aurora
- Create an **aurora** read replica of your RDS DB, then when there is no replication lag promote it to its own DB

From on-prem - SIMILAR
- From on-prem: backup to S3 and restore from backup
- From on-prem: Use **aws_s3 aurora extention**

For both
- Use DMS if both are active