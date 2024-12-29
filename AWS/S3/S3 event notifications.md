- S3 events are things like uploading an object S3:ObjectCreated, or deleting an object
- You can also add filters like \*.jpg object created event
- You can create as many as you want.
- Notifications usually take seconds, but can take minutes to arrive at destination.

**Key services that can receive events**
- Lambda
- SNS
- SQS

In addition, you can configure all events to go through **amazon event bridge**, which can forward the event to all or some of a variety of other services. 
Using event bridge you gain advanced JSON filtering, like via metadata, size

IAM resource access policies need to exist on the SNS topic/SQS queue/lambda function to allow the bucket to send data to the service.
