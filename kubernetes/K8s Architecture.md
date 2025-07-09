🔵🔹🔷 🔵 ➡️ ⏺️
☑️ ✔️ 🔴 ⭕
•
‣
→
⁕

# ⏺️ Kubernetes is a Cluster
- **Cluster** host all the resources and infrastructure.  
- `Cluster = Master Node/Control Plane + Worker Node/Node`

### ➡️ 1. Control Plane Component

##### 🔷 apiserver
- Stores cluster state(etcd) and exposes k8s API.
##### 🔷 etcd
- Persistent storage for cluster state.
##### 🔷 Controller  Manager
- Runs Core control loops(controllers).
- 
##### 🔷 Cloud Controller Manager
##### 🔷 Scheduler


### ➡️ 2. Worker Node Component
##### 🔷 kubelet

##### 🔷 kube-proxy 
- Maintains network rules on nodes, network rules allows network communication to your Pods from network sessions inside or outside of your cluster.
- Runs Pods on worker nodes.



### ➡️ Container Runtime


### ➡️  Addons 
- DaemonSet, Deployment, etc...





