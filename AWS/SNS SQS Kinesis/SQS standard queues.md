SQS = simple queue service

**What is a queue**
A list of messages: producers send messages, consumers "poll" messages and process them.

Standard Queue is the oldest offering and is used to **decouple applications**
- Unlimited throughput
- Unlimited messages in queue
- Low latency
- Max 256KB per message
- Default retention 4 days, max 14 days.
- Guarantees "at least once" delivery - some messages might be duplicated
- Best effort ordering - message ordering not guaranteed
- Messages are not deleted until a consumer specifically deletes them - if they dont the message will remain after being processed.

Messages are produced using the SDK (SendMessage API).
Consumers - processes running on EC2, Lambda can poll for up to 10 messages at time.
They process the message and then use the DeleteMessage API to delete it.

**Strong pattern: ASG paired with SQS**
1. Setup an ASG and set the EC2 as consumers.
2. Put on a cloudwatch metric of QueueLength (ApproximateNumberOfMessages), set an alarm for a specific threshold
3. Cloudwatch alarm triggers ASG to scale horizontally.


**Decouple frontend and backend with SQS**
![[SQS standard queues.png]]
