**At rest encryption**
- DB master & replicas encryption using keys stored in AWS KMS, defined at launch
- If master is not encrypted, read replicas cannot be either
- To encrypt master you must take a snapshot and restore as encrypted

**In-flight encryption**
- TLS ready by default

**IAM**
You can use IAM roles OR username/pw to connect to RDS

**Security groups**
You can use SGs as firewalls to control RDS/Aurora access

**No SSH**
Except on RDS custom where you get OS access

**Audit logs**
Can be enabled and sent to CloudWatch Logs for retention