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

### ➡️ Service Example

```yml
apiVersion: v1
kind: Service
metadata:
  name: order-service
spec:
  type: ClusterIP
  selector:
    app: order-app
  ports:
    - port: 80
      targetPort: 8080
```

- label for the Pod is defined in the Deployment's `.spec.template` 🔴
- This lable is used in the Deployment's `.spec.selector` and Serive's `.spec.selector` 🔴

##### 🟦 type: ClusterIP

- Default type.
- Means:
  - Accessible inside cluster only
  - Gets stable internal IP
  - Used for microservice-to-microservice communication

##### 🟦 selector

```yml
selector:
  app: order-app
```

- Service looks for Pods having:
  - `app=order-app`
- So Service connects automatically to:

```yml
order-pod-1
order-pod-2
order-pod-3
```

- If new Pod is created → automatically added.

##### 🟦 ports

```yml
ports:
  - port: 80
    targetPort: 8080
```

- port:
  - Service port
  - Other pods inside the cluster call this port
  - This is the port exposed by the Service object
- targetPort:
  - container port
  - The Service forwards traffic to this port inside the Pod
  - This must match the **Deployment’s** `ports.containerPort` in Deployment🟠
- Flow becomes:

```yml
order-service:80 → PodIP:8080
```

#### 🟦 Visual Flow

```java
Client (payment-service)
        ↓
order-service (ClusterIP)
        ↓
kube-proxy load balancing
        ↓
One of the 3 Pods
        ↓
Container (Spring Boot)
        ↓
Application logic
```

- Suppose, Payment service calls:
  - `http://order-service/api/orders`
- **Step 1:** DNS Resolution
  - Kubernetes DNS converts `order-service` into IP Address(Service IP) `10.96.20.15`
- **Step 2:** kube-proxy Takes Over
  - **kube-proxy does**
    - Watches the Service + Endpoints
    - Reads Pod IPs from Endpoints
    - Routes traffic accordingly
  - kube-proxy sees traffic to `10.96.20.15:80`
  - It checks Service endpoints and endpoints list looks like:
  - Pod IP + Port

    ```yml
    10.1.1.2:8080
    10.1.1.5:8080
    10.1.1.9:8080
    ```

  - So all three Pods are listening on different IPs (i.e., each Pod has its own unique Pod IP)
  - And they are listening on the same port 8080, which is the container port
  - This 8080 belongs to the container running inside the Pod
  - It is NOT a Pod port
  - All containers inside a Pod share the same Pod IP
  - Containers can listen on:
    - Same port (if only one container in the Pod)
      `PodIP:8080`
    - OR different ports (if multiple containers in Pod)
      ```yml
       Pod IP: 10.1.1.5
       Container A → 8080
       Container B → 9090
       Container C → 3000
      ```

- **Step 3:** Load Balancing
  - kube-proxy chooses one, example `10.1.1.5:8080`
- **Step 4:** Pod Receives Request
  - Traffic goes to **Pod IP**:`10.1.1.5`
  - Inside Pod:
    - Container listening on `8080`
      - Remember this `8080` is Container's Port not the Pod's Port if only one container in the Pod
      - If more then one container then one container is having port `8080` and other container will have  
        different ports.(Container A -> `10.1.1.5:8080`, Container B -> `10.1.1.5:9090`, Container C -> `10.1.1.5:3000`)
    - Now Spring Boot is running and handles request
