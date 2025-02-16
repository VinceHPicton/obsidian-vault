
**Using SQS as a buffer for handling DB load spikes**
- Because SQS standard queue is **infinitely scalable** you can just write DB queries which are to be performed to the queue to provide an infinite buffer, and know that they will be executed later.
- You can have 1 ASG which writes messages to the queue and another ASG which works through the queue and executes the queries
- There is a limitation that you will be providing feedback to users that (for example) their order was completed when it wasn't actually in the DB yet.
![[SQS + ASG patterns.png]]

**Decoupling front and backend**
If you are able to process backend requests asynchronously you can do this with SQS queue paired with ASG backend:
![[SQS + ASG patterns2.png]]