Simple notification service.

**What problem does this solve?**
Similar to kafka, SNS provides a pub/sub architecture for **one service to trigger an action in any number of receivers** by publishing 1 message.
That means the sending service does not have to directly contact all the subscribing services, it just makes 1 call.

![[SNS.png]]

- An event producer sends a message to a topic, and all subscribers to the topic will receive the message.
- You can have 12,500,000 subscriptions per topic and 100k topics per account - **do not need to remember these numbers**
- Many AWS services can send data directly to SNS, eg CloudWatch alarms, Lambdas, many more.

**Types of topics**
- Standard
	- Can take all kinds of subscribers
- FIFO
	- Only SQS can subscribe

**How to publish a message**
- Topic publish (using AWS SDK)
	- Create topic
	- create subscriber(s)
	- Publish to topic
- Direct publish - this is for a mobile app to receive the notification
	- Publish to a **platform endpoint**, not a topic


