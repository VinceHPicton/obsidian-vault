This is SSO for AWS - it lets you have one login for your organisation and all the AWS accounts in it, and you can use this for anything else with SSO like MS Outlook etc.

You can use the AWS Identity store for your users or another like MS active directory.

When you SSO into AWS you will then be able to choose which specific AWS account you want to login to (without further passwords) - this is highly recommended whenever you have multiple AWS accounts.

So when you login to AWS you get this to choose which console you want:
![[AWS IAM Identity Centre.png]]

You can also provide permission sets in identity centre to give specific user groups permissions for different things.
![[AWS IAM Identity Centre-1.png]]

You can further refine permissions with **ABAC (attribute based access control)** - to give users permissions based on their title or something.