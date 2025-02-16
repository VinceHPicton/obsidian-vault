**IAM policy conditions** - apply a permission only if a criteria is met, or for example do a blanket allow but deny for users without a specific condition (like MFA)
![[Advanced policies.png]]

**IAM for S3**
You can define specific permissions for specific objects within a bucket


**Resource policies and aws:PrincipalOrgID**
You can use PrincipalOrgID to define access to resources only if an account is a member of a specific [[AWS Organisations|AWS Organsation]] 
![[Advanced policies2222.png]]
