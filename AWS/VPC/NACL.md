NACLs (network access control lists) are like a firewall which control traffic to and from **subnets**
- A subnet can only have 1 NACL, but a NACL can be used for many subnets.
- A newly created NACL will deny everything
- NACLs are a great way to block a specific IP from accessing a subnet.


**NACL are stateless, security groups are stateful**
NACLs are applied to specific subnets and are stateless, unlike security groups which apply to specific resources and are stateless.
Stateless means they do not save any state about the requests, which means that when a response to a specific request comes back (which will point to the ephemeral port on the client) the NACL must specifically also allow that response back in. Same applies for service inside the VPC responding to an unsolicited request.
![[NACL & Security groups statefulness.png]]


**NACL rules**
- NACLs have a list of rules which are numbered (1-32766)
- The first rule down the list which matches the request determines the decision, number 1 is highest priority and so on.
- AWS recommends adding rules in units of 100 - first rule at 100, next rule at 200. 
- If a higher priority ALLOWS and a lower priority DENIES, the request will **still be allowed** because the allow rule was higher priority.

**The default NACL**
- **Accepts everything inbound and outbound** for the subnets its associated with - so it's completely open.
- This makes sense because otherwise to do anything on AWS you'd first have to manually create a NACL.
- Do NOT modify the default NACL, just create a new one.
![[NACL & Security groups default nacl.png]]

**Ephemeral ports**
When a client sends a request out to say URL:3306, it will also open and provide an ephemeral port, to which the response should be sent. It will be added as a header on the initial request, and will be a big number (between 32768 - 60999 or 49152 - 65535). The ephemeral port is **only open for the duration of the connection.**
![[NACL & Security groups ephemeral port.png]]


**Multiple subnets and NACLs**
Important to note that if you have many subnets sharing NACLs, the NACL needs to allow all the different combinations of communication between subnets.
![[NACL1.png]]