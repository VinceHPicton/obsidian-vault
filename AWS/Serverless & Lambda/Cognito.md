Authentication/auth token swapping through AWS

You have user pools of 2 types:

**Cognito user pools**
- This is your users of your apps
- Can inegrate with **API gateway** and **ALB**
![[Cognito2.png]]

**Cognito Identity Pools**
- For giving users direct access to aws resources, eg a private S3 bucket
- IAM policies that the credentials provide are defined inside cognito and can be customized based on user_id
- You can create default IAM roles for authenticated or guest users incase they dont have a specific defined role.
![[Cognito.png]]



**Cognito vs IAM** These terms mean Cognito in exam:
"hundreds of users"
"mobile users"
"authenticate with SAML"


**Key points for exam:**
- Create user base for web and mobile app
- enable row level security in dynamoDB for fine grained access: give user access to read/edit only records with specific ID prefix for example
- Integration with API gateway or ALB