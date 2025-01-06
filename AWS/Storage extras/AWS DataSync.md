This is **scheduled** data syncs that can be setup to take place from anything, to anything. Schedule a sync hourly, daily, weekly etc.

**Sync between**
AWS service <-> AWS service (no agent)
AWS service <-> on-prem (agent needed)

**Relevant services**
- S3 - all tiers
- EFS
- FSx

**Key point** for exam: *Only* DataSync **preserves file metadata** like permissions on copying

The agent is again software running on-prem eg a VM which acts as the client to do DataSyncs.

Exam hint: You can use AWS Snowcone with agent pre-installed if customer **doesn't have the network bandwidth**

![[AWS DataSync.png]]