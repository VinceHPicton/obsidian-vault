A route table is a **set of rules** (called routes) which define how network traffic **FROM** your subnet is directed.
Route tables do not control direction of traffic into your VPC.

Every [[Subnets|subnet]] within a VPC **must** be associated with a route table, if you do not define one, the main route table for the VPC will be used.