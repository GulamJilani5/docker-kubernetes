### ✅ Cluster = Master + Nodes

A Cluster is the whole Kubernetes system.
**It includes:**
**Master Node (Control Plane):** Manages the cluster (scheduling, scaling, updates).
**Worker Nodes:** Where your applications (containers) actually run.

### 🧩 Pod

Pod is the smallest deployable unit in Kubernetes.
It can hold one or more containers (usually just one).
All containers in a pod share the same **network IP**, **storage**, and **namespace**.
Think of a pod as a wrapper around your container(s).
