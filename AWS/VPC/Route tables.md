A route table is a **set of rules** (called routes) which define how network traffic **FROM** your subnet is directed.
Route tables do not control direction of traffic into your VPC.

Every [[Subnets|subnet]] within a VPC **must** be associated with a route table, if you do not define one, the main route table for the VPC will be used.

Route tables match according to which rule is **most specific** to the IP destination.

For example:
- `10.0.1.0/24 → local`
- `10.0.0.0/16 → nat-xxxxxxxx`

If a packet is destined for `10.0.1.5`, it matches **`10.0.1.0/24` first** because it’s more specific than `10.0.0.0/16`.

If no match is found, the packet is dropped.