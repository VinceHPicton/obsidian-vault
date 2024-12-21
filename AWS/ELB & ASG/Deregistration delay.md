Also known as connection draining, this is where you define a delay period which occurs before the instance shuts down, in which any existing connections are able to complete, but the load balancer won't forward any *new* traffic to the instance.

The drawback is you now have to wait that amount of time before the EC2 is actually stopped.

Can be set 1-3600 seconds, default 300 (5 mins). Can be turned off by setting value to zero.

If your user requests do not take long, you can set this value low.