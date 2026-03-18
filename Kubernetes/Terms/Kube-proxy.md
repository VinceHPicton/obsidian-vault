The Network Rules Manager

The **kube-proxy** handles **networking for Services** on each node.

It ensures that traffic gets routed to the correct pods, using methods such as:
- **iptables**
- **ipvs**
- (less common today) **userspace proxying**

### **Key responsibilities**

- 🔁 **Implements Kubernetes Services**
    - ClusterIP
    - NodePort
    - LoadBalancer
- 📡 **Load balances traffic** between pods in a Service
- 🔧 **Maintains NAT rules** so that:
    - Services map to Endpoints
    - NodePort maps to a Service

### **Think of kube-proxy as:**

> “The node’s network router that knows how to send Service traffic to the right pod.