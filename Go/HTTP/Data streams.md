### **What is a data Stream?**

A **stream** is a continuous flow of data that is read sequentially. It's different from a regular data structure like a string or an array because:

1. **You can only read forward.** No random access (unlike a string, where you can access any character).
2. **Once read, the data is gone.** There’s no built-in storage—it’s read and discarded unless you save it.
#### **Examples of Streams**

- **A network connection**: Data arrives in chunks, and you process it as it comes.
- **A file being read line by line**: You read and process each line, but previous lines aren’t stored in memory unless you explicitly keep them.
- **An HTTP response body (`resp.Body`)**: Data is received over the network and read into memory in chunks.

