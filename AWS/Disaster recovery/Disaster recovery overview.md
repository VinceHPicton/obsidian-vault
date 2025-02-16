RTO = Recovery time objective (how long it takes to recover)
RPO = Recovery point objective (when your last point in time was that you can recover back to)

![[Disaster recovery overview.png]]

There are 3 ways to have backups set up
- On-prem => on-prem - very expensive
- on-prem => Cloud (hybrid recovery)
- Cloud => Cloud (via using multi region AWS)

There are 4 main disaster recovery strategies from an on-prem
1. Backup and Restore
2. Pilot Light
3. Warm Standby
4. Multi-site/hot site

**Backup and Restore**
- This backing up your data to the cloud every so often
- One way to do this is using [[AWS Snow devices|AWS Snowball]]
- This has a high RPO - in a disaster you will lose a lot of data as backups are infrequent.
- It also has a high RTO - it could take days to set back up
- This is a pretty **cheap** way of having backups.

**Pilot Light**
- This is having a small version of your app always running in the cloud (a pilot light is like the tiny flame always on in a boiler)
- This pilot light will usually just have your critical core of services - no EC2s running
- Faster than backup and restore but very similar

**Warm Standby**
- Full system is running alongside in the cloud but at a minimal size
- Faster again to recover as cloud services will just scale up

**Multi-site**
- 2 full scale apps are running - on prem and on the cloud
- You route traffic to both of them so make use of both already
- Very fast RTO - your cloud resources just scale up.

**Final option: just have all infrastructure in the cloud with multi-region**
Can use any of the multi-region DB features to replicate data across regions, like Dynamo global tables, or aurora global.

A couple of tips:
- Using Route 53 you can just change your DNS record to a backup data centre
- Use CloudFormation or Elastic Beanstalk to quickly spin up a full environment.