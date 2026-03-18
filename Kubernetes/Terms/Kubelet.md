The node [[Agent]]

The **kubelet** is the primary agent that runs on each Kubernetes worker node.  
Its job is to **ensure that containers are running exactly as the Kubernetes control plane expects**.

### **Key responsibilities**

- 📝 **Reads PodSpecs** (from the API server or from manifest files)
- 🚀 **Starts containers** using the container runtime (containerd, CRI-O, etc.)
- 💬 **Reports node & pod status** back to the control plane
- 🔄 **Restarts failed containers**
- 📦 **Manages liveness/readiness/startup probes**
- 💾 **Mounts volumes**, handles secrets/config maps on the node
- 📡 **Runs the CNI plugin** to set up pod networking

### **Think of kubelet as:**

> “The node’s supervisor that keeps pods healthy and running.”