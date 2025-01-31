In asynchronous mode a Lambda gets an event queue.

You can set a reserved concurrency at the function level, and you should do this because you can only have **up to 1000 concurrent executions across all functions in a region**.

Therefore if you let one function take up all the slots your others will all get throttled too.

If more requests than the maximum come in, they will be **throttled**, this:
- If synchronous invocation => return ThrottleError 429
- If asynchronous invoation => retry and then go to DLQ (dead letter queue) which is where failed requests are sent.

**Retries**
- Lambda will retry the event for up to 6 hours
- It will retry after 1 second, exponentially increasing this delay between retries until it hits 5 minutes.

**Cold starts & provisioned concurrency**

A cold start occurs when a new lambda instance is created, it has to load code and dependencies which takes time, making the first request slower than the rest.

To solve this problem you can provision concurrency to allocate some instances in advance, so no cold starts.
App auto scaling can manage concurrency via scheduled or target based utilization, these 2 types are explained in [[ECS Auto Scaling]]

These graphs show these concepts visually, here the top of the graph is the region wide 1000 concurrency limit.

![[Lambda Concurrency & async mode.png]]