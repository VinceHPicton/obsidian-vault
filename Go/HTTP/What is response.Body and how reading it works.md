As soon as we start reading from `resp.Body`, we are **pulling data from the network**. Before we interact with `resp.Body`, the data isn't fully received yet—it’s sitting in **a TCP buffer** managed by the operating system, waiting to be read.

Here is a sendRequest function in Go, we will look at how it works:
```
func sendRequest(client *http.Client, req *http.Request) ([]byte, error) {
	resp, err := client.Do(req)
	if err != nil {
		return nil, err
	}

	defer func () {
		if err := resp.Body.Close(); err != nil {
			log.Fatalf("failed to close response body: %v", err)
		}
	} ()

	if resp.StatusCode < 200 || resp.StatusCode > 299 {
		log.Printf("received code: %d from: %v", resp.StatusCode, req.URL)
	}

	var buf bytes.Buffer
	if _, err := io.Copy(&buf, resp.Body); err != nil {
		return nil, err
	}

	return buf.Bytes(), nil
}
```

### **Step-by-Step Breakdown of What Happens**

#### **1. The HTTP Request is Sent**

When you call:

`resp, err := client.Do(req)`

- The Go HTTP client (`client.Do(req)`) establishes a TCP connection to the server.
- It sends the HTTP request over the network.
- The server processes the request and starts sending back the response **in chunks**.

At this point, `resp.Body` is an **open stream** connected to the network, but we haven’t actually read any of the response data yet.

---

#### **2. The Response Starts Arriving (Buffered by the OS)**

- The HTTP response data **does not arrive all at once**.
- It is **received in chunks** and temporarily stored in a **TCP receive buffer** managed by the OS.
- The size of this buffer depends on network conditions, OS settings, and the TCP window size.

So at this stage:

- The **response headers** are already parsed (so `resp.StatusCode`, `resp.Header`, etc., are available).
- The **response body is waiting in the OS’s buffer**, but we haven’t read it yet.

---

#### **3. Reading from `resp.Body` Triggers Data Transfer**

When we execute:

`var buf bytes.Buffer io.Copy(&buf, resp.Body)`

- `io.Copy` starts reading from `resp.Body`, which pulls data **out of the OS buffer** and into `buf.Bytes()`.
- The OS then **removes that data from the buffer** to free space for more incoming data.
- If the response is larger than the buffer, new chunks arrive from the network as we keep reading.

This is why **reading from `resp.Body` actually triggers network activity**—we're fetching data as needed.