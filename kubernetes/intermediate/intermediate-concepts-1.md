### 🌐 Service

- A Service exposes your Pod(s) to other pods or external users.
- Since pods are ephemeral (they can die and restart), services provide a stable IP/DNS.
- **Types:**
  - ClusterIP (internal only)
  - NodePort (expose via static port on node)
  - LoadBalancer (cloud-based external IP)

### 🔁 Deployment

A Deployment ensures that your desired number of pod replicas are running.

**Handles:**

- Scaling up/down
- Rolling updates
- Rollbacks
- It's how you deploy and manage pods in a controlled way.

### ConfigMap
