This is the ability to set consumes to "wait" for a message if there are none in the queue at the time of polling.
They can wait from **1-20 seconds**

The reason you do this:
- Reduce latency - if a consumer is waiting when a message comes in it will instantly begin processing, rather than having to wait in queue for a new poll.
- Reduces number of API calls since more will be successful on average.

Preferable to set max long polling of 20 seconds.

Can be enabled for a queue level or the API level (ie changing the API parameters)