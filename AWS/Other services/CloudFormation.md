This is basically AWS' version of Terraform, but it only works with AWS. It's Infrastructure as Code (IaC) tool.


- One benefit of it is you can set up thing to be deleted between 5pm-8am for example - to save cost.
- Also being declarative like terraform, you dont have to worry about the ordering of how services are created, like you would in the console - eg can't create a LB without first creating a Target group etc.


**The CloudFormation service role**
By default, CloudFormation assumes the permissions of the user calling it when it's run, but maybe we don't want to give every user running CloudFormation all the permissions needed for CloudFormation.

In this case we can use the CloudFormation service role, which is just a normal IAM role designed for CloudFormation to assume, giving it the perms it needs to adjust services.
This helps us maintain the principle of least privilege - not giving out major permissions to users without need.

The user calling CloudFormation must have the **iam:PassRole** permission.
