Backup is a service that lets you automate backups of data to S3 using **"backup plans"** without having to write scripts and do manual tasks for your backups. It enables PITR (point in time recovery) for supported services, backup frequency configured by you.

You can schedule backups and/or do them on-demand

Backup plans include things like frequency of backup and retention period


**Backup vault lock**
Applies WORM (write once read many) policy to your bacups
With this active not even the root user can delete a backup.