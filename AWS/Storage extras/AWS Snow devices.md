AWS offers:
- Snowcone (smaller)
- Snowball edge (larger)
- Snowmobile (largest) - maybe discontinued

These are physical devices that can be used for compute, **importing or exporting data to S3** (not any other services). 

These are physical devices aws sends out to a customer, you upload your data to it and send it to AWS to upload to your S3 bucket for example.

This is used where data transfers over the internet would take an huge amount of time, eg **over a week**.

To do this you:
- Request a snowball device from AWS console
- Install snowball client to your server
- Connect snowball and copy files over
- Ship device to AWS
- Data is loaded to S3
- Snow device is completely wiped

**Edge computing**
Edge locations are things like a ship or in a mine - where little or no internet access is available.

An AWS snow device can be used to run your lambdas or EC2s at the edge location for example.

Uses eg: data processing, ML.


**Exam question: using snowball to import to Glacier**
You can't do it directly, you just set use a lifecycle policy on the S3 bucket to move the imported items straight to glacier.