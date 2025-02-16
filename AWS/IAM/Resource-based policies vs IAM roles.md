- The key difference here is that when the principal service or user assumes an IAM role, **they give up all their original permissions and take all the permissions on the role instead.**
- When using a resource-based policy, the principal **does not do this**

**Using a service cross-account**
- The user can either take a role that allows them to access the cross-account action
- Or the resource can have a resource-based policy that allows the account

**Resource-based policies only exist on some services**
- Lambda, SNS, SQS, S3, API Gateway, and more


**Exam thing: EventBridge needs permissions to apply its event to targets**
It can do this either with a IAM role or using a resource-based policy.