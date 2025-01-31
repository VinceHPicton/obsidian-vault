A subnet is a range of IPs within your VPC, like 10.1.0.0/24 (which means 10.1.0.0 - 10.1.0.255)

- A **public subnet** is a subnet which has a [[Route tables|route]] to the internet via an [[Internet Gateway]].
- A private subnet has no such route.

**Important IP reservations**
AWS reserves 5 IP addresses in any CIDR range: the first 4 and last 1.

If your range was  10.1.0.0/24 then reserved are:
-  10.1.0.0 - address of the network itself
-  10.1.0.1 - reserved for AWS VPC router
- 10.1.0.2 - reserved for mapping to amazon-provided DNS
- 10.1.0.3 - reserved for future use by AWS
- 10.1.0.255 - the network broadcast address, AWS does not support broadcast so this address is just out of use.

Therefore remember that if you needed eg 29 addresses (in exam), you would need to choose a CIDR range that provides 29 + 5 = **34** addresses.
- Choosing /27 provides 2^5 = 32 addresses, because after the 5 reserves you only have 27
- Therefore you must choose /26 

