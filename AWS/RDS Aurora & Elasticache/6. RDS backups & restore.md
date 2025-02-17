There are 2 options for backing up:
- Automated
	- Daily full backup
	- Transaction logs backed-up every 5 mins
	- Able to restore to any point
	- 1-35 days retention, set zero to disable feature (NOT long term backups)
- Manual
	- Eg before a schema update
	- Retain as long as you want (LONG TERM backups possible)

Exam trick: a stopped RDS DB is far more expensive than a snapshot. For long periods of stopping, take a snapshot and delete the instance.

Aurora backups are the same as for RDS except that automated backups **cannot be disabled**


**Restoring**
- Restoring a snapshot creates a brand new database.
- You can also export a snapshot of an RDS to S3 for long term storage and restore to a new instance.

**Aurora Database Cloning**
- Clone an aurora cluster faster and cheaper than using a snapshot & restore
- Uses "copy-on-write" protocol:
	- Initially the clone points at the same data volume as the original (no copying of data)
	- When updates are made to the clone, only then is new storage allocated and data copied
- Use case would be creating a staging DB from production without impacting prod