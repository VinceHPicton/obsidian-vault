GuardDuty is a **threat detection service** which works by analysing your logs from various sources using ML, finds things like suspicious IPs.

You turn it on and it just works, you dont need to do anything, but it costs money.

**It has dedicated "finding" for cryptocurrency attacks**

At minimum it analyses:
- VPC Flow Logs
- CloudTrail logs
- DNS logs
- There are many more sources of data it can optionally use, eg S3 logs.

It will then trigger an EventBridge event if it detects something suspicious.

![[GuardDuty.png]]
