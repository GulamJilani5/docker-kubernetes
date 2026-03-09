⏺️ ➡️ 🟦 🔵 🟢 🔴 ⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️ Service Mesh

- **Service-to-service traffic(East-West traffic)** refers to the communication between microservices running in pods inside a Kubernetes cluster.
- Service Mesh manages communication between internal microservices(Pods) inside the k8s cluster.
- **Service Mesh Tools**
  - istio, Linkerd, AWS App Mesh, Azure Service Mesh.
- Service mesh

## ➡️ Sidecar Proxy

- In a Service Mesh, a sidecar proxy is deployed inside each pod alongside the main application container.
- Service Mesh secures internal service-to-service communication using Mutual TLS (mTLS).

## ➡️ Features of Service Mesh(Managed By Sidecar Proxy)

#### 🟦 Service Discovery

- Allows services to find and communicate with each other automatically without hard-coding service addresses in the application code.

#### 🟦 Load Balancing

- Distributes incoming traffic evenly across multiple instances of a service.

#### 🟦 Circuit Breaking

- Prevents a service from being overloaded when another dependent service fails or becomes slow.

#### 🟦 Fault Tolerance

- Ensures that services continue functioning even when some dependencies fail.

#### 🟦 Metrics and Tracing

- Provides observability into the system.

#### 🟦 Security
