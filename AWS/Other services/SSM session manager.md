This service provides a 3rd way we can use to connect to our EC2 instances - the other 2 being EC2 instance connect or a bastion host. It requires the **SSM agent** software to be installed on the EC2.

Crucially, using SSM session manager, **we can keep port 22 closed** on the EC2 instance, which means better security.

It supports all 3 OS's - mac, windows and linux.

We need to create and add an IAM role to the EC2 instance to allow it to talk to session manager.