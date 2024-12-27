The best of way of starting up your EC2s is with a "golden [[AMI (amazon machine image)|AMI]]" and user data scripts for dynamic config.
- The golden AMI contains all OS config, dependency installs etc which are the same across all your EC2s
- The userdata does anything else

For RDS, you will want to have a snapshot you restore from which contains all your schemas etc.

For EBS again you will want a snapshot