Key thing to note: kinesis data streams to data firehose is great because firehose pools the data, and eg every 1 minute you could then upload to S3 and have a lambda transform it somehow first.

![[Big data ingestion pipeline example.png]]
