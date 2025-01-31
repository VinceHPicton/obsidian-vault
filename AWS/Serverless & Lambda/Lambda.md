- Virtual functions - not servers like EC2
- 15 min max running time
- Pay per request and compute/call time
	- Free tier: 1,000,000 Requests and 400,000 GB seconds of compute
	- This means if you had functions of all 0.5 GB RAM, you'd get 800,000 seconds of compute using them for free
- Integrated with many many AWS services
- Support for many languages, notably Node.js and Python, Custom runtime API for misc langs
- Increasing RAM will also improve CPU and network - less to config
- Lambda containers are possible by ECS/Fargate are a better way to run them.

Main integrated services: unsure if need to remember
- API gateway
- Kinesis
- S3
- SNS
- SQS
- Cognito
- Cloudwatch event + eventbridge
- Cloudwatch logs
- Cloudfront
- DynamoDB

**Example uses for Lambda**
- CRON job that runs every hour
- 
![[Lambda1.png]]