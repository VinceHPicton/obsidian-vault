This is microsoft AD but on AWS

Active directory is more than just SSO:
It's a database of objects - printers, computers etc, with centralised security.


AWS provides 3 directory services, one is a proxy, one is AWS managed, one is "simple AD"
The simple cannot be joined with your on-premise AD
- AWS managed active directory
- AD connector (proxy)
- Simple AD


**Setting up AD with IAM identity centre**
You can either connect to an AWS managed AD centre, or connect to a self-managed one