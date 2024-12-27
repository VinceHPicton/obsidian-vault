A developer focused view of AWS services, it manages services to abstract them away from the developer so they don't need to worry about them, meaning the developer only needs to worry about their app code.
The user still maintains control of configuration, AWS handles scaling, health monitoring, OS config of instances etc.

**Components of EB**
- Application - this is a collection of EB components like environments, versions, configs
- App version (which iteration you are using)
- Environment
	- Tiers
	- Can create multiple envs like dev and prod

**Supported platforms**
Go, PHP, Java, docker container(s), .NET, node.js, many more

**Web tier vs worker tier**
Essentially worker tier is where EC2 (workers) handle processing messages from SQS queue, like data analysis not client requests. Web is just standard client requests handling. Web env can puhs messages for worker tier to handle.

**Deployment modes**
- Single instance: used for dev env, cheaper
- High availability mode: for production, 
![[Elastic Beanstalk instances modes.png]]