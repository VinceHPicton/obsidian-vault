
- EC2 (elastic cloud compute) lets you spin up virtual machines (VMs) in the cloud.
- EC2 can grow and shrink whenever you need (elastic) to meet demand.
- You can create one and have it running in minutes.
- You only pay for exactly what you use - no longer buying whole web servers.

**Pricing options**
1. On-Demand: most expensive
2. Reserved capacity: you keep a fixed amount of compute available for 1 or 3 years, saves up 72% off on-demand price.
3. Spot-price: you use excess unused capacity when it’s available, eg running calculations that you can have done anytime, so you have them done very cheaply at super off-peak times. Saves up 90% from on-demand
4. Dedicated server: you rent exclusive use of physical machine with amazon, great for when you want super-high security for compliance.

**EC2 consists of several other services**
- Renting VMs (EC2)
- Storing data on virtual drives (EBS)
- Distributing loads (ELB)
- Scaling service using auto-scaling groups (ASG)


**Config options**
- OS choice: windows, Linux, MacOS
- CPU
- RAM
- Storage space


**AWS CLI**
- Remember principle of least privilege, dont grant access more than needed
- Assign users to groups and give the group permissions


- Secret access key = the password for using the CLI
- EC2 access keys should never be shared
- One developer should have one access key like passwords
- You can use AWS CLI on windows mac and linux, or on an EC2 instance.


**Roles in EC2**
Roles are basically identities which hold certain permissions which something can assume for a period of time (a session). Something assumes a role for a session and when that session ends the thing loses those permissions. 
They can also allow cross-account access.

- An AWS service, or a user, can assume a role, so an AWS service could assume a role allowing it to create s3 buckets for example
- Roles are the preferred method for security, because they are temporary, and mean eg an EC2 service doesnt need to hard-code keys to have access to another resource.
- Policies (IAM) control a role’s permissions, you can add policies to a role and this will take effect immediately (persumably because it reads the policy document each time before doing anything)
- You can also attach or detach roles from an EC2 instance without having to terminate or stop it

  

**Bootstrap scripts**
Bootstrap scripts are just scripts you can run on an EC2 the moment it starts up, eg a bash script for a linux one to install stuff


**Stopping and starting EC2 instances effects on IP**
When you stop and restart an EC2, its public IP may be changed, but its private IP wont be.


**Instance types - dont need to remember classes**


**General purpose class** (T and M and A1 classes):
Balance between compute memory and networking, good for web servers or code repos.

**Compute optimized** (C class):
Good for compute-intensive tasks where high perf processors are needed
Eg batch processing workloads, high perf web servers, gaming servers, media transcoding

**Memory optimized** (R (RAM) class, X class, z class)
High performance DBs

**Storage optimized**
Databases, caching

Compare instances: [https://instances.vantage.sh/](https://instances.vantage.sh/)

**EC2 Naming convention:** 
m5.2xlarge ->
- m = class
- 5 = generation (aws improves each class over time)
- .2xlarge is size.
  

**Key port conventions**

- SSH: 22 - log into a linux instance.
- FTP: 21 (file transfer protocol)
- SFTP: 22 (secure file transfer protocol - FTP over SSH)
- HTTP: 80 (unsecured)
- HTTPS: 443
- RDP: 3389 (Remote desktop protocol - log into a windows instance)

  

For networking comms: OSI Model: [https://en.wikipedia.org/wiki/OSI_model](https://en.wikipedia.org/wiki/OSI_model)

  

**SSH on EC2 summary**

- If on mac, linux, windows 10+ you can use SSH
- If on windows < 10 you cannot use SSH
- You can use PuTTY on any windows but not linux/mac
- You can use EC2 instance connect on any OS.

  

**Spot instances and terminating them**

- You can create either a one-time or a persistent spot instance request.
- The one-time will go away once it has been fulfilled - ie it started instance(s) outlined in the request.
- When/if these instances are interrupted (due to price) or stopped, they wont be restarted.
- The persistent will keep the defined instances running as long as the price requirement is met, and persistent requests have a start/end date.
- You can only cancel a request (one-time or persistent) which is open, active, or disabled, the other 3 states are failed, cancelled and closed.
- If you want to stop instances from a persistent request, you need to cancel the spot instance request first, otherwise it will keep trying to make new instances after you stop them.
- Also, if you cancel a spot instance request, any running instances will not be terminated, you need to do that yourself.

  

**Spot fleets**
Spot fleet = some spot-price instances + (optionally) some on-demand instances

You define pool(s) of size, AZ, OS for AWS to choose from.

It can then spin up instances to attempt reach your max capacity or max cost.

The launching strategies are:
- Lowest cost: always choose cheapest pool
- Diversified: spread load across many pools for resilience
- Capacity optimized: choose pool with most capacity
- priceCapacityOptimized: choose cheapest from the list of pools with highest capacity available.


**EC2 hibernate mode**

Pause and reboot an EC2 instance much faster. Especially good for services that take ages to boot.

Cannot hibernate for more than 60 days.

As if the instance never stopped - copies the RAM state onto the EBS disk, available for all instance types, disk must have the space needed for the RAM.

The root EBS volume must be encrypted, and must be an EBS volume.

Most EC2 classes are supported, bare metal type instances aren’t supported.

  


