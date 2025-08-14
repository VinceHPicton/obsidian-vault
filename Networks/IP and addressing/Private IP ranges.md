The IANA (internet assigned numbers authority) made rules that said certain IPv4 blocks should be used for private LAN and public internet addresses.

Private IPs are only allowed certain values:
- 10.0.0.0 - 10.255.255.255 (10.0.0.0/8) are allowed for big networks
- 172.16.0.0 - 172.31.255.255 (172.16.0.0/12) AWS default VPC range
- 192.168.0.0/16 - home network range

All the rest are public.