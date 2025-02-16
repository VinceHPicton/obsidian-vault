Permission boundaries restrict what a user/role can do, regardless of its specific IAM policy - it puts a boundary around what is allowed.

These are applied **only to roles or specific accounts**, NOT groups

So they work alongside SCP organisation policy and the IAM policy itself, to restrict what a role/user can do.
![[IAM Permission boundaries.png]]