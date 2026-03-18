These are machines in the [[Cluster]] which run the containers for your application

They need the [[Kubelet]] and [[Kube-proxy]] [[Agent]] software installed (these are daemons) to work as part of the cluster.

- **kubelet** is the _node agent_, it actively reports status and executes instructions from the control plane (master node).
- **kube‑proxy** behaves like a **networking agent**: it runs on each node, watches the API server for Service/Endpoint changes, and updates the node’s network rules accordingly.