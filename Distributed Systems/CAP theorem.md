CAP theorem relates to distributed systems during a [[Network partition|network partition]] event, CAP means:
- Consistency - every read gets the most up-to-date write or an error
- Availability - Every request receives a response that is not an error.
- Partition tolerance - the system can continue to operate despite the presence of a network partition


CAP theorem is ultimately about how to handle a [[Network partition]], which is certain to happen at some point in a distributed system due to packet loss, network outage, etc. 

When a [[Network partition]] occurs do you choose to:
- Reject requests (error) because you can't be completely sure the data you respond with is correct (thereby choosing availability over consistency)
OR
- Respond with data which is possibly out of date (thereby choosing availability)

