
A static, public IPv4 address you can rent, which is yours as long as you dont delete it.

You are charged for it as long as you do not use it (encouraging use rather than hogging).

You can use it to mask a failure of a service - by immediately assigning your elastic IP to a healthy instance.

Using an elastic IP is generally bad and indicates poor architectural decisions.

It’s better to have a random public IP and register a DNS name for it,

Or use a load balancer and have use a public IP at all.

You can also only have 5 elastic IPs for an AWS a/c, but this can be requested to increase.