**Lambda, SNS and SQS.**
- You can use Lambda process events from either of SNS or SQS.
- In SQS, the consumer (here a lambda) has to actually manually delete a message once it's completed, this could result in infinite retries if it fails, so need to configure sending the message to a DLQ (dead letter queue) from SQS after enough retries.
- In SNS, it's the Lambda which has to send it to the DLQ in SQS after 3 failures.

**Remember the SNS + SQS fan out pattern**
Rather than sending to 3 different queues, the true sender sends to 1 SNS topic.


**S3 event notifications**
S3 events can be handled by many services, but it's essential to remember they can be handled by **any or all of**:
- Lambda
- SQS
- SNS
- EventBridge

key use case: generate thumbnails of uploaded images

With EventBridge you get all the other functionality like archiving and replaying events.


**Intercepting API calls**
You can use EventBridge to intercept dangerous actions from CloudTrail - eg delete table.

![[Event Processing in AWS.png]]