Where synchronous is where one app directly calls another, asynchronous (also called event based) is where one app adds to an event queue, and another app can pick up and process that event in its own time.

A key advantage of event based is **handling spikes** in application traffic. Eg if suddenly some users all upload 1000 videos that must be processed, in synchronous this could cause a crash. So event based **decouples** your applications.

In AWS you can do this with:
- SNS queue model
- SNS pub/sub model
- Kinesis real-time streaming model