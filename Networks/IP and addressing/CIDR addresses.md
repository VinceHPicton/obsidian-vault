Classless Inter-Domain Routing, named as such as it replaced the old "classful" way of IPv4 routing. 

CIDR ranges are a representation of an **IP address range**, for example 123.123.123.0/24 represents a range of usable addresses from 123.123.123.1 - 123.123.123.254, where 123.123.123.0 is the address of the **network**. 

.255 is missing because 123.123.123.255 (the final IPv4 address) is used to broadcast to all addresses on the network.

The /24 means the first 24 bits are used to identify the network - the **network prefix**, and the final 8 bits are for specific devices on the network, think of it as: 123.123.123.xxx
Or in bit terms: 11111111.11111111.11111111.xxxxxxxx, giving us 256 addresses (excepting broadcast and network address)

/23 for example, would mean the first 23 bits are for the network:
11111111.11111111.1111111x.xxxxxxxx
leaving us 512 IP addresses: 123.123.123.XXX and 123.123.124.XXX (excepting broadcast and network address)

0.0.0.0/0 means **all** IP addresses. The first zero bits are the network address, leaving all 32 bits as variable.

122.149.196.85/32 means **one single IP** address

![[CIDR addresses2.png]]