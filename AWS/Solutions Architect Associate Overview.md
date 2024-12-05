
Compute, storage, networking and databases are the bread and butter service types of this exam.


**Well-architected framework**

You can go to [https://aws.amazon.com/whitepapers/](https://aws.amazon.com/whitepapers/) to read whitepapers. And here is the one you need on the well-architected framework READ THE NIGHT BEFORE EXAM [https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html?did=wp_card&trk=wp_card](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html?did=wp_card&trk=wp_card)


**The six pillars of the well-architected framework:**
- Operational excellence (running and monitoring to deliver business value, continually improving processes)
- Security
- Reliability (uptime)
- Performance efficiency (using computing resources efficiently)
- Cost optimization
- Sustainability (environmental) 

Cloudwatch logs are AWS preferred soln for logging
Route 53 service lets you route domain names using DNS


**AWS infrastructure: building blocks of AWS**
Region = a physical location like London, Northern Virginia. It consists of 2 or more availability zones

Availability zone (AZ) = one or more data centre which will be so close together that they’re still counted as 1 zone. Separate AZs are separated by a meaningful distance, many kms, but all AZs within a region are within 100km of eachother. 

Edge locations = endpoints for AWS that are used for caching content, there are many more edge locations than regions, typically this consists of CloudFront  


**Cloud responsibility:**
Its similar to renting a car, you’re responsible for what you do with the car.

A general rule for answering whether the user is responsible: ask yourself can you do this thing yourself in the AWS management console? Do you have control of this?

Encryption is a shared responsibility.


**Key services for exam:**

**Compute**
- EC2
- Lambda
- Elastic Beanstalk

**Storage**
- S3
- EBS (elastic block store) - basically a virtual harddisk attached to VMs
- EFS (elastic file service)
- FSx
- Storage Gateway

**Databases**
- RDS
- DynamoDB (Non relational)
- Redshift (database warehousing tech)

**Networking**
- VPCs (virtual private clouds_ - basically virtual data centres in the cloud
- Direct Connect (a way to directly connect your HQ on prem datacentres to AWS)
- Route 53 - a way of doing DNS
- API Gateway (a serverless way of replacing your web servers)
- AWS Global Accelerator    

  
Many of the questions on the exam are unscored so if you feel like you’re getting loads wrong, it may be because they are unscored (too hard and are in there to let AWS collect data)

  