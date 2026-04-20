Eviction policies are used to determine what to do when the **cache is full**


### LRU - least recently used
Simple and pretty effective, a good default.
Bad for scan workloads

### LFU - least frequently used
Keeps popular items, but is more complex. Ignores "trends" eg an item was very used but hasn't been for ages

### FIFO - first in first out
Delete the **oldest** item regardless of usage.
Simple but very dumb

### LIFE - last in first out
Delete the newest item regardless of usage.
Simple but very dumb

### RR - random replacement
Extremely cheap operation
Surprisingly good for massive workloads when complexity of a better strategy might have a higher cost than its worth.


# Reality
Systems use hybrid approaches, like approximate LRU