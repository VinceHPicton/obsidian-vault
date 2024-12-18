This is where traffic is evenly balanced across instances in several AZs.

![[Cross-zone load balancing img.png]]

By default it's enabled for application load balancers at **no extra cost** which is cool because typically data transfer across AZs does have a cost.

It's not enabled by default for network load balancers or gateway load balancers, and with these, if you enable it, the data transfer does cost money.