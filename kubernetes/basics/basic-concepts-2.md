⏺️ ➡️ 🟦 🔵 🟢 🔴 ⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️ Pod

- Think of a pod as a wrapper around your container(s).
- Pod is the smallest deployable unit in Kubernetes.
- It can hold one or more containers (usually just one).
- All containers in a pod share the same **network IP**, **storage**, and **namespace**.

### ➡️ Pod IP is NOT stable

- Every Pod in Kubernetes gets its own IP. That IP is ephemeral
- If:
  - Pod crashes
  - Pod is deleted
  - Node fails
  - Deployment recreates it
- A new Pod is created
- It gets a new IP address
- So Pod IP is not reliable for direct communication.

### ➡️ Pod Networking

- Container do not have IP Address. Pod IP is used for container
- Inside a Pod, containers are differentiated by PORT, because they all share the same Pod IP.
- Containers are distinguished by port numbers
