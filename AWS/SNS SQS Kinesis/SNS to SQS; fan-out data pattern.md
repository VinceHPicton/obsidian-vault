If you want to send a message to multiple SQS queues, best way to achieve this is to send a message to a SNS topic which all the SQS queues are subscribers of.
- No data loss (makes it atomic), and fully decoupled.
- SQS allows data persistence, delayed processing and retries.
- Can add more SQS subscribers whenever
- SQS queue policy must allow SNS to write.
- Can send messages to SQS queues in other regions.

**A key application**
S3 buckets have a limitation whereby you can only set 1 event rule per bucket + prefix (eg mybucket/images).
So if you want to notify more than 1 thing for eg an item added to that bucket + prefix, you have to use fan-out.
![[SNS to SQS; fan-out data pattern 1.png]]


**Kinesis firehose**
![[SNS to SQS; fan-out data pattern.png]]

**SNS FIFO**
SNS can have ordering just like with [[SQS FIFO queues]] but the subscribers to this topic **can only be a SQS standard or SQS FIFO queues**
Limited to same throughput as SQS FIFO
- You can also get fan out + ordering and deduplication by making many SQS FIFO queues the subscribers.

**SNS message filtering**
A SNS topic subscriber can use a JSON policy to apply filters to the messages it receives.
If no filters exist, the subscriber receives every message sent to the topic.

For example you might want email service to only receive messages with `filter: email`
Or you might want to split the SNS messages into separate SQS queues for cancelled, placed, declined order types.

![[SNS to SQS; fan-out data pattern 2.png]]