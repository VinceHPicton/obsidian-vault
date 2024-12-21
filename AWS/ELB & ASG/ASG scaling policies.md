Ways you can setup the ASG to scale:

**You can create any mix of these rules if you want**
- Dynamic scaling
	- Target tracking scaling
		- It **tracks a target metric**, eg average ASG CPU to stay around 40%, and adjusts number of instances accordingly
	- Simple scaling
		- Adds or removes instances when a specific alarm is triggered, eg cloud watch alarm triggered for >70% CPU, add 2 instances, or <30% take away 1.
	- Step scaling
		- Adjusts the number of instances in different predefined **steps** based on how far the metric deviates from thresholds. eg CPU >90% add 3 instances, CPU >70% add 2 etc.
- Scheduled scaling
	- When you know your usage comes in predictable waves like a time of day
- Predictive scaling (ML driven)
	- Let AWS analyse your usage patterns and auto scale for you.

**Good scaling metrics**
- CPUUtilisation
- RequestCountPerTarget - if you know an optimal number of requests for an instance
- Network throughput in or out - if you know network is the bottleneck

**Scaling cooldown**
A period after any scaling action takes place where any further alarms are ignored, to allow the recent change to take effect. Default it's 300 seconds.

Note: important to use a ready-to-use AMI (do not have a load of user data steps that must be done) to reduce configuration time for new instances which will allow a small cooldown period.