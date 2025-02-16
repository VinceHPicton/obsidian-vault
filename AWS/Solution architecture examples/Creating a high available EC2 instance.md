2 methods, both involve switching an elastic IP to the new instance on fail: 
1. Use a cloudwatch alarm or event which will detect some metric about your EC2 showing failure, in this case a lambda can run which will spin up a new instance in a new AZ, and attach the Elastic IP
2. Use an ASG, spread across 2+ AZs, with min, max, desired = 1 instance. Put into the EC2 userdata the code to attach the elastic IP to itself. If the instance fails, the ASG will bring up a new one.

**Finally, what if the EC2 has an EBS volume?**
EBS volumes exist in 1 specific AZ, so if the new EC2 is in a new AZ, we need to snapshot and copy over the EBS to the new AZ.
We can use the 2nd method, and use **lifecycle hooks** on the ASG:
- On a **termination** event of EC2, the hook will trigger and **snapshot** the EBS
- On **launch** event, we can set a hook which creates a new EBS volume from the snapshot and attach to the new EC2 instance.