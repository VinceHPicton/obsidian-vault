[[OSI model (7 network layers)|Layer 3]] (network layer) load balancer

It's a single point of access for your fleet of network virtual applicances.
Key exam facts:
- **Transparent network gateway** (this means it's invisible to traffic - it **cannot** block traffic directly like an ALB, and is not detectable)
- It's **also a load balancer** distributing traffic to it's target groups
- **Only** uses the **GENEVE** protocol on **port 6081**

Possible target groups:
- EC2 instances
- **Private** IP addresses

![[Gateway load balancer (GWLB) img.png]]