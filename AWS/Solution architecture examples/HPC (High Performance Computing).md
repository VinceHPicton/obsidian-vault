This is about how we can combine different AWS services to do HPC, for things like computational chemistry, financial modelling etc.

**Data transfer methods**
How we can transfer our data for computations to the cloud
- Direct Connect (DX) - 1 GB/s transfers over private AWS network
- Snowball/Snow devices - for transferring PetaBytes of data to the cloud
- [[AWS DataSync]] move large amounts of data from on-premise to S3, EFS, FSx


**How to use EC2 effectively**
Use spot-instances/spot-fleets to get cost effective compute
Use **EC2 placement groups** which are clusters of EC2s on the same rack, which can communicate with very high bandwidths and low latency.

**EC2 enhanced networking**
How can we further increase EC2 networking speeds?
- Use an ENA (enhanced network adapter) up to 100 GB/s
- There is a legacy Intel 82599 VF thing 10gb

EFA (Elastic fabric adapter)
- This is an even further improved ENA for linux only EC2s
- Especially good for clustered nodes

**Storage in HPC**
EC2 instance store - capable of even higher IOPS than the best EBS (io2 256000)

Network storage:
- S3, EFS, FSx for Lustre - an HPC optimized File System

**Automation and orchestration**
AWS Batch - supports multi-node parallel jobs - spread work acrosss many EC2s

AWS ParallelCluster:
- Able to enable EFA (elastic fabric adapter) on the cluster to improve network perf
- ParallelCluster is an open source management tool for HPC