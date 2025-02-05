VPC = virtual private cloud

- You can have up to 5 VPCs within 1 region, but this can be increased
- 5 max CIDR per VPC
	- Min size /28 (16 addresses)
	- Max /16 (65536 addresses)
- Because VPC is private, not public, only the private IPv4 ranges are allowed:
	- 10.0.0.0 - 10.255.255.255 (10.0.0.0/8) 
	- 172.16.0.0 - 172.31.255.255 (172.16.0.0/12) 
	- 192.168.0.0/16 
	- See [[Private IP ranges]]

**Your VPC CIDR ranges should never overlap with your other networks, eg corporate network**
