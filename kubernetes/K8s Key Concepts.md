🔵🔹🔷 🔵 ➡️ ⏺️
☑️ ✔️ 🔴 ⭕
•
‣
→
⁕

# ⏺️ Some Important key concepts in K8s

### ➡️ ReplicaSet
- We, Developer, do not required to explicitly create the ReplicaSet.
- We work at the `Deployment.yml` abstraction level. **Deployments** automatically create ad manage `ReplicaSet` for us.
- Number of Pods in `.spec.replica` inside the `Deployment.yml` is the replicaset.
- `kind:ReplicaSet` 


### ➡️ DaemonSet
- A **DaemonSet** ensures that a copy of a specific pod runs on every node (or on selected nodes) in a Kubernetes cluster.  
- Think of it like this: If you have 5 nodes in your cluster, and you create a DaemonSet, it will automatically deploy 1 pod on each of those 5 nodes.  
- A **DaemonSet** is its own kind of resource, just like `Deployment`, `StatefulSet`, or `Job`.  
- If you're using `kind: Deployment` in your YAML file, you're not using a **DaemonSet**.  
- Must explicitly define `kind: DaemonSet` in your YAML if you want to use **DaemenSet**.
- 
**Summary**

| Feature    | DaemonSet                        |
|-----------|----------------------------------|
| Purpose    | Run 1 pod per node               |
| Use Case   | Logging, monitoring, networking  |
| Implicit?  | ❌ No                            |



### ➡️ StatefulSet 
- A StatefulSet is a Kubernetes workload controller used to manage stateful applications.
- It is similar to a Deployment, but with extra guarantees for stateful behavior.
- As a developer, we must explicitly define it using `kind: StatefulSet`.
-  Any stateful app that needs persistent data, Stable network identity, Stable pod names (hostnames), Ordered startup and shutdown.

**Use Case**

| Use Case            | Example                      |
| ------------------- |------------------------------|
| Databases           | MySQL, PostgreSQL, MongoDB   |
| Message brokers     | Kafka, RabbitMQ              |
| Distributed systems | Cassandra, Elasticsearch     |



### ➡️ Services

### ➡️ Storage 

### ➡️ Volumes

##### 🔵 Storage Class

##### 🔵 Volumes Types
- 🔷 Persistent volumes
- 🔷 Projected Volumes
- 🔷 Ephemeral Volumes

##### 🔵 PVC(Persistent volumes Claim)
##### 🔵 Dynamic Volume Provisioning


### ➡️ Cronjob

### ➡️ Ingress




