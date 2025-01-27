
**ECS tasks invoked by event bridge**
Essentially serverlessly handle some processing for any object added to S3 - eg making a DB record of that object's address and name.
![[ECS solution architectures.png]]

**ECS tasks invoked by EventBridge on a schedule**
Batch processing, made serverless
![[ECS solution architectures2.png]]
**ECS paired with SQS queue**
Similar to scaling your SQS queue with EC2 instances to process them, you ca do this with an ECS service which auto scales based on queue length.
![[ECS solution architectures 1.png]]

**Intercept stopped ECS tasks using eventbridge (failure notifs)**
![[ECS solution architectures 2.png]]