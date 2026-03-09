⏺️ ➡️ 🟦 🔵 🟢 🔴 ⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️ Service Mesh

- **Service-to-service traffic(East-West traffic)** refers to the communication between microservices running in pods inside a Kubernetes cluster.
- Service Mesh manages communication between internal microservices(Pods) inside the k8s cluster.
- **Service Mesh Tools**
  - istio, Linkerd, AWS App Mesh, Azure Service Mesh.
- Service mesh

## ➡️ Sidecar Proxy

- In a Service Mesh, a sidecar proxy is deployed inside each pod alongside the main application container.
- These Sidecar proxies handle traffic to and from the microservices running in pods, intercepting requests and responses.
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

## ➡️ Components of a Service Mesh

#### 🟦 Data Plane

- The Data Plane is responsible for routing and managing traffic between microservices running inside pods. It is implemented using sidecar proxies

#### 🟦 Control Plane

The control plane is responsible for configuring, managing, and monitoring the proxies. It includes components like a control plane API, service discovery, and configuration management.
