
Virtual [[Network cards]], bound to a specific AZ - can only be attached to EC2 instances in that AZ.

They're like separating the IP part from the EC2 instance, meaning you can move the ENI to a new instance if one fails (just like removing the physical hardware component from one computer and plugging it into another one), meaning the system is only down for a few seconds.

An ENI can have:
- A public IPv4
- A primary private IPv4
- Multiple secondary private IPv4
- One elastic IPv4 per private IPv4
- Security groups
- A MAC address (media access control) this is basically a unique identifier for devices in a given network, network cards always have one, along with generally devices that have a network interface, like a smartphone, network interfaces built into computers etc.