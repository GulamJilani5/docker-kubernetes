⏺️ ➡️ 🟦 🔵🔹🔷 🔵 ☑️ ✔️ 🔴 ⭕ • ‣ → ⁕

# ⏺️ Ingress

- It exposes Http/Https routes from the cluster to services within the cluster.
- The ingress controller routes HTTP requests to the correct service.
- Traffic routing is controlled by the rules defined in the **Ingress Resource**(`YML`).

## ➡️ Why Use Ingress (Kubernetes)

### 🟦 Single Entry Point 🔴

- It allows you to configure a single entry point for multiple services, making it easier to manage external access to applications.

### 🟦 TLS/SSL Termination 🔴

- The client communicates with the Ingress using HTTPS, and the Ingress decrypts the request and forwards it to internal services using HTTP, eliminating the need for TLS certificates on individual services or pods.

- **Ingress can terminate TLS/SSL, meaning:**
  - Client sends HTTPS request
  - TLS encryption exists until the Ingress
  - Ingress decrypts the request
  - It forwards plain HTTP to the Kubernetes Service/Pods

```txt
Client (HTTPS)
      ↓
Ingress Controller (TLS termination happens here)
      ↓
Service (HTTP)
      ↓
Pods (HTTP)
```

- **Why this is useful**
  - Pods do not need TLS certificates because Pods are not publicly exposed
  - Only Ingress is exposed to the internet
  - Internal cluster network is trusted/private
  - Certificate management is centralized
  - Less CPU overhead on services

### 🟦 Path-Based Routing

- It routes traffic to different services based on the request path.
- Example:
  - `/app1` → Service 1
  - `/app2` → Service 2

### 🟦 Host-Based Routing

- It routes traffic based on the requested host or domain name.
- Example:
  - `app1.example.com` → Service 1
  - `app2.example.com` → Service 2

### 🟦 Load Balancing 🔴

```text
Client
  ↓
Cloud Load Balancer (optional)
  ↓
Ingress Controller
  ↓
Kubernetes Service
  ↓
Pods
```

#### 🔵 Cloud Load Balancer(External Load Balancer)

- This is the entry point from the Internet into your Kubernetes cluster.
- It distributes traffic across multiple nodes of the cluster.
- AWS ELB / ALB / NLB, Azure Load Balancer

```text
Internet
   ↓
Cloud Load Balancer
   ↓
Node1
Node2
Node3
```

- If one node fails, traffic goes to another node.
- So this balances across nodes, not pods.

#### 🔵 Ingress Controller

- The ingress controller routes HTTP requests to the correct service.

#### 🔵 Kubernetes Service

- This is done using kube-proxy (iptables/IPVS).
- K8s Service balances traffic between pods of the same application.

### 🟦 Annotations (Customization)

- Ingress resources can be customized using annotations to configure additional settings such as:
  - Rewrite rules
  - Custom headers
  - Authentication
  - Other controller-specific configurations.

## ➡️ Ingress Controller vs Spring Cloud Gateway

- They often work together
- **Ingress** handles **cluster entry**, while **Spring Cloud Gateway** handles **API-level** routing and policies.

```text
Client
   ↓
Cloud Load Balancer
   ↓
Ingress Controller
   ↓
Spring Cloud Gateway
   ↓
Kubernetes Service (user-service, order-service, etc.)
   ↓
Pods (instances of the microservice)
```

### 🟦 Ingress Controller

- It acts as an edge component for Kubernetes clusters(services).
- It manages external HTTP/HTTPS traffic into the cluster(services).
- Configuration is mainly done through **Ingress resources** (`YAML`).

### 🟦 Spring Cloud Gateway

- It is a Java-based API Gateway.
- Built on Spring Cloud Gateway and Spring Boot.
- Highly customizable capabilities for microservices using Java filters, predicates, and custom logic.
