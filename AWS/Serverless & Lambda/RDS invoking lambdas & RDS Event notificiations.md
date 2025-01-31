

**Invoking Lambdas from RDS and Aurora**
- Supported for **RDS for Postgres** and **Aurora for MySQL** only
- Let's you process **data events** in the DB, like INSERT new user
- Set up within DB by connecting to it, not from AWS console.
- RDS instance invokes function, so **must allow traffic from RDS to the lambda**
- and must have correct IAM policies to give **permissions** to invoke the lambda.
![[RDS invoking lambdas & RDS Event notificiations.png|200]]

**RDS event notifications**
With these you do not have access to any actual DB data, only events like DB created, stopped, started etc.
- Near real-time (5 mins max)
- Event categories suported:
	- DB instance
	- DB snapshot
	- DB parameter group
	- DB security group
	- RDS proxy
	- Custom engine version
- Notify SNS or subscribe to events with eventbridge

![[RDS invoking lambdas & RDS Event notificiations 1.png|250]]