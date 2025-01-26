SNS
- Is essentially kafka - pub/sub to topics model
- Can be used in front of many SQS queues
- Messages are not persisted

SQS
- Consumers **poll data** and delete messages from the queue manually
- Ordering only on FIFO queues.

Kinesis
- Data is persisted up to 365 days and can be replayed
- Data grouped into **shards**
- Used for **real-time** data streaming for big data analytics