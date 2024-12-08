Elastic Block Storage volumes are [[Network Drive|network drives]] for EC2 instances

Some EBS can be attached to multiple instances.

They are in 1 specific place in the world, so they are **locked to 1 availability zone**. You cannot attach an EBS in us-east-1a to an EC2 in us-east-1b. To do that you must **snapshot it**.

Free tier: 30GB of free EBS storage of type general purpose (SSD) or magnetic per month.

Because the drive is connected via the network there can be latency on transactions.

It can be easily detatched from 1 EC2 and attached to another.

They have provisioned capacity - eg 100GB, but you **can** increase the capacity at a later time.

![[EBS volumes img.png]]
**Delete on termination setting**
Controls whether an EBS volume is deleted when the EC2 instance is terminated
- For the root volume, by default it is ON (it is deleted on instance termination)
- For other volumes, by default it is OFF (not deleted)
- This can be controlled in the AWS console, these are just default settings.

So if you want to preserve the root volume you must change this option.