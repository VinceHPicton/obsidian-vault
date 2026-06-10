They fulfil different roles, and therefore many projects use both.

RabbitMQ is a traditional message broker, you'd use it for just async messaging between services, and it's quite similar to [[1. SQS standard queues]]. It naturally supports retries and Dead Letter Queues, whereas Kafka does not (you'd have to build it yourself). Messages **flow through** RabbitMQ - once a consumer processes the message, it's gone.
Ordering in RabbitMQ is done by default, messages are FIFO.

Kafka is essentially a distributed append-only log. Retention of the logs can be configured between seconds and indefinitely. It's actually a simple broker in terms of it's just a log, and the consumers are deciding what to read and when. Messages **live in** Kafka - they aren't consumed, they're kept.
Ordering in Kafka is only within partitions, you can control which partition a message goes to, and that partition is ordered as a queue is (FIFO), but the ordering across partitions is not preserved.