Block an object's version deletion for a specific time period

Allows you to adopt WORM model (write once read many)
Requires versioning to be enabled

**Retention mode - compliance**
- Set a retention period which cannot be changed by anyone, even root user
- Versions cannot be deleted or overwritten by anyone

**Retention mode - Governance**
- Less strict than compliance
- Most users cannot overwrite or delete object version, but some users with special permissions can.

Retention period: protect an object for a fixed period

**Legal hold**
- Protect an object indefinitely, **independently from its retention period**. For example a court document
- Can be free placed or removed if user has s3:PutObjectLegalHold IAM permission.