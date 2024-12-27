- Starting with the [[Stateful application stack]] we can add an [[EFS (elastic file system)]] to store images, this avoids the issue that would arise from one EBS per EC2 meaning images cant be found by all instances.
- Each EC2 must be given an [[ENI (Elastic network Interface)]] in order to connect to the [[EFS (elastic file system)|EFS]] via the network.

![[Stateful with images stack.png]]