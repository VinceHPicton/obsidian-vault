Regions are like us-east-1

**Reasons you might choose a specific region**
- Availability of the services you want, not all regions have all services
- Proximity to your customers - reducing latency
- Compliance with laws in the area - gov might require you to store data in that country
- Cost: some regions are cheaper than others!

**Regions, AZs and datacentre hierarchy**
![[AWS regions img.png]]

- A region is a geographical area like London, Ireland, Canada Central
- Within a region there are **always 3 to 6** availability zones (AZ)
- Within an availability zone there is 1 or more data centres with redundant power, networking and connectivity
- AZs are connected with ultra high bandwidth, ultra low latency networking (so they can act like they are 1 data centre)
