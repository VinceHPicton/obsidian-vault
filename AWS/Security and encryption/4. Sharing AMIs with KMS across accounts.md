If an AMI snapshot is encrypted with a KMS key.
- You must modify the image attributes to add a **launch permission** which allows the target AWS account
- Must share the KMS key, and the IAM role in new account must have permissions:
	- DescribeKey
	- ReEncrypted
	- CreateGrant
	- Decrypt
- When launching EC2 in new account, you can then use a KMS key in new account to encrypt a new snapshot.