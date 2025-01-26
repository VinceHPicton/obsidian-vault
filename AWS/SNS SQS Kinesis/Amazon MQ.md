This a managed **message broker service** for users who want to use RabbitMQ or ActiveMQ, not the aws proprietary SNS/SQS, eg because they dont wanna rebuild their apps to use SNS/SQS

- Amazon MQ doesn't scale as much as SQS/SNS 
- Has a queue and topic features to mimic SNS/SQS
- It runs on servers, not in a serverless way, so can be made multi-AZ with failover:

![[Amazon MQ.png]]