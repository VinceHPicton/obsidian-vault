Internet [[protocol]] is a set of rules that defines how data packets should be addressed and routed through the internet. 

Things that IP does as part of the data transfer process:
- Gives packets a source and destination **IP address**, either IPv4 or IPv6
- **Fragmentation** and reassembly: if data is too large to send in 1 packet IP dictates how to split the data up into different packets. It adds metadata to each packet to achieve this, which are:
	- Identification: each packet created from the fragmentation has the same identifier
	- Fragment offset: tells the recipient the position of each fragment relative to the start of the data, allowing reassembly.
- The **routing decision process** is also part of IP, this is used by each forwarding router in the path the packet take to determine *the route* the packet will take through the internet.
	- It does this essentially by sending the packet to the closest match it can find in its routing table. Eg for a packet with IP 115.232.010.55 it will look for a subnet with an address like 115.232.010.0/24 (which means 115.232.010.xxx), and that node will hopefully find a better match.

IP adds a variety of metadata to it's encapsulated data (the payload) alongside source/destination addresses, these are represented by specific bits in the sequence. 
- Version (4 bits) - 4 or 6
- Header length (4 bits)
- Total length (16 bits) - length of header + payload, max length of IPv4 packet is 65535 bytes due to 16 bit maximum
- Identification (16 bits)- used for fragmentation
- Flags (3 bits) - also used for fragmentation
- Fragment offset (13 bits)
- Time to live (TTL) (8 bits) - specifies maximum number of hops (between routes) the packet can make before being discarded, TTL decremented by 1 every hop, prevents endless circulating of packets.
- **Protocol used in payload** (8 bits) - tells recipient how to read the packet, can be 6 = TCP, 17 - UDP etc
- Header checksum (16 bits) - used for validating header is correct - if data was lost in transit.
- And several more...

Version 4 (IPv4) was the first major version of IP
Version 6 (IPv6) is it's successor, both are still used today