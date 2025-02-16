= Managed Streaming for Kafka

An alternative to kinesis data streams but with some differences, like kafka allows up to 10MB messages

You can either:
- manually create clusters
	- Data stored on EBS for as long as you want
	- Deploy into your VPC and replicate up to 3 AZs
	- Get automatic recovery 
- Or use it **serverlessly**

**Differences between MSK and kinesis data streams**
- Kinesis has 1MB messages, kafka default 1MB, up to 10MB
- Kinesis uses shards, kafka uses partitions
- Kinesis uses TLS (SSL), MSK TLS or plaintext
- Both use KMS for at rest encryption

Consume data from MSK with:
- Apps on ECS, EKS, EC2
- AWS Glue
- Flink
- Lambda