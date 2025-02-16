This itself isnt a service, it uses CloudFormation to bring up and shut down resources on a schedule to save costs.
**Key use case: shut down EC2 instances outside business hours.**

The schedules are held in a DynamoDB table, it uses instance tags and Lambda to stop/start resources.
Supports **EC2, ASG, and RDS**
