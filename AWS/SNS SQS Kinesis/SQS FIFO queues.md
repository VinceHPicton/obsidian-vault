This is the other type of queue different to [[SQS standard queues]], where ordering is guaranteed.
FIFO = first in first out.

- Because of the ordering the throughput is limited to 300 messages/second without batching or 3000 msgs/s with batching.
- Able to include "exactly-once" capability by sending a deduplication ID with messages, preventing message duplicates (with same ID) being processed within a 5 minute window.
- There is a mandatory parameter "message group ID" which causes messages with the same group ID to be processed in order.
- Queue name must end with ".fifo" eg "myqueue.fifo"