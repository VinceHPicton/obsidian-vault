
It's a network [[file system]] (NFS), **bound to one region** which can be bound to many 100s of EC2 instances **within that region**.

You can define mount targets to all [[AWS regions and availability zones (AZ)|AZ]]'s in the **region**, or a subset.

![[EFS mount targets.png]]
*Note how we can't add anymore mount targets, as we are already mounting to all 3 AZs in the region*

- It can only be used for linux instances as it uses a [[POSIX]] filesystem
- It's more expensive than EBS (3x gp2 cost), but you can leverage cost savings by archiving rarely used files.
- Uses a security group to control access to EFS.
- Encrypted at rest with KMS.
- Scales automatically, pay per used GB, no capacity planning.

**Throughput modes:**
- Elastic - Automatically scales up and down, for unpredictable workloads
- Bursting - throughput grows with storage, but can burst a lot higher when needed.
- Provisioned - for when you want to define a set throughput regardless of storage

**Performance modes:**
- General purpose - web server
- Max I/O - highest latency, throughput, highly parallel - big data

**Storage tiers:**
You can set **lifecycle policies** for your EFS, which defines when files are automatically moved to **infrequent access** tier storage, and then finally to **archive** tier, if they are not being accessed after X number of days.

**Zoning**
As shown above, you may limit your EFS to fewer, or just one, AZ, which might be useful to save money if it's just used for dev and not prod for example.