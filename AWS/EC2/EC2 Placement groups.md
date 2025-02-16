
Used for if you want to control exactly where EC2 instance hardware is assigned.

There are 3 strategies:

- **Cluster**: puts instances into a low-latency group in a single AZ, vulnerable to failure as all share the same hardware, super low-latency, high throughput network
    
- **Spread**: opposite of cluster, spreads the instances into different AZs so very unlikely for them all to fail at same time, limited to **7 instances per AZ per group** (so that they are actually spread out?)
    
- **Partition**: spreads instances into different physical racks such that instances in 1 partition do not share hardware with those in another. You can have up to **7 partitions per AZ**, up to 100s of instances, you could have some partitions in different AZs in a region.
	- Why would you use partition? Because using spread limits you to 7 instances per AZ, if you want 100s of EC2s in a region you can't use spread, so you use partition, it still achieves increased availability over cluster as it's over multi-AZ.
	- Also: different partitions are on different server racks, so you are protected against a rack failure.