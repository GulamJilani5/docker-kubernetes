🔵🔹🔷 🔵 ➡️ ⏺️
☑️ ✔️ 🔴 ⭕
•
‣
→
⁕


# 🔄 Kubernetes Concepts:
| **Component**  | **Purpose**                                                                             |
| -------------- | --------------------------------------------------------------------------------------- |
| **Cluster**    | Group of Master and Node(s) working together                                            |
| **Master**     | Controls and manages the Kubernetes cluster (API Server, Scheduler, Controller Manager) |
| **Node**       | Worker machine that runs containerized applications (managed by Master)                 |
| **Pod**        | Smallest deployable unit; holds one or more containers                                  |
| **Service**    | Provides stable networking and load balancing for pods                                  |
| **Ingress**    | Routes external HTTP(S) traffic to internal services                                    |
| **CronJob**    | Schedules and runs jobs at specific times or intervals                                  |
| **Deployment** | Manages pod replicas and handles rolling updates                                        |



# ✅ Cluster = Master + Nodes
A Cluster is the whole Kubernetes system.
**It includes:**
**Master Node (Control Plane):** Manages the cluster (scheduling, scaling, updates).
**Worker Nodes:** Where your applications (containers) actually run.

# 🧩 Pod
Pod is the smallest deployable unit in Kubernetes.
It can hold one or more containers (usually just one).
All containers in a pod share the same **network IP**, **storage**, and **namespace**.
Think of a pod as a wrapper around your container(s).

# 🌐 Service
A Service exposes your Pod(s) to other pods or external users.
Since pods are ephemeral (they can die and restart), services provide a stable IP/DNS.
Types:
ClusterIP (internal only)
NodePort (expose via static port on node)

LoadBalancer (cloud-based external IP)

# 🚪 Ingress
Ingress is a smart router.
It manages external HTTP(S) access to your services.
**You define rules like:**
/api → backend-service
/ → frontend-service

Works with an **Ingress Controller** (e.g., **NGINX**, **Traefik**).
Replaces the need for multiple **LoadBalancers**.

# 🕒 CronJob
 A **CronJob** runs tasks on a schedule (like **Linux cron**).

**Useful for:**
- Backups.
- Reports.
- Periodic data processing.
- schedule: "0 0 * * *" # daily at midnight

# 🔁 Deployment
A Deployment ensures that your desired number of pod replicas are running.

**Handles:**
- Scaling up/down
- Rolling updates
- Rollbacks
- It's how you deploy and manage pods in a controlled way.

### ReplicaSet

### DaemonSet

### StatefulSet

### Storage

### Volumes




