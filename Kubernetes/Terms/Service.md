A networking abstraction which **exposes a set of pods**

It provides a stable IP and DNS name, and load balances traffic across your pods.

It does this by identifying which pods have a common "app" label

```
# my-k8s-cluser_service.yaml
...
selector:
	app: my-app-name
```


It's the typical and by far main way to expose your pods to the internet or yourself, for access by users.


## 🔹 Why Services exist (the key problem)

Pods are **ephemeral**:

- They get new IPs when recreated
    
- They scale up/down dynamically
    

If you tried to hit Pods directly:

- You’d need to constantly track changing IPs
    
- Your app would break during updates