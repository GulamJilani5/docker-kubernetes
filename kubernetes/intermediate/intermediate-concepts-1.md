⏺️ ➡️ 🟦 🔵🔹🔷 🔵 ☑️ ✔️ 🔴 ⭕ • ‣ → ⁕

# ⏺️ Service

- A Service exposes your Pod(s) to other pods or external users.
- Since pods are ephemeral (they can die and restart), services provide a stable IP/DNS.
- **Types:**
  - ClusterIP (internal only)
  - NodePort (expose via static port on node)
  - LoadBalancer (cloud-based external IP)

### ➡️ Why We Need Service

- Because Pods are dynamic.
- Imagine our service(reactjs)
  - ReactJS → Call `10.1.2.45` (Pod IP)
  - Pod crashes(dies) → New Pods created and Now Pod Ip is: `10.1.3.78`
  - ReactJS still calling older IP `10.1.2.45` → Application breaks.
- So we need service
  - Stable IP
  - Stable DNS name
  - Load balancing across Pods

##### 🟦 Stable IP

- When we create a Service:

```
kind: Service
name: order-service
type: ClusterIP
```

- Kubernetes gives it a permanent IP(i.e: service IP)
  - order-service → `10.96.45.12`
- This IP:
  - Never changes, Even if Pods die, Even if new Pods are recreated
- So instead of calling:
  - Pod IP -> `10.1.1.2`
- We call:
  - Service IP -> `10.96.45.12`
  - Even if Pods change and it IP also gets change — Service IP remains same.

##### 🟦 Stable DNS Name (Even Better)

- Instead of remembering IP, Kubernetes gives:
  - `http://order-service`
- Spring Boot app:
  - `http://order-service/api/orders`
- That’s it. No IP needed.
- Even if Pods change — DNS remains same.

##### 🟦 Load Balancing Across Pods

- Suppose 3 Pods exist:

```
  order-pod-1
  order-pod-2
  order-pod-3
```

- Now 3 requests come:

```
Request 1 → order-service
Request 2 → order-service
Request 3 → order-service
```

- Kubernetes automatically distributes:

```
Request 1 → pod-1
Request 2 → pod-2
Request 3 → pod-3
```

- We did NOTHING, Service does that automatically.
