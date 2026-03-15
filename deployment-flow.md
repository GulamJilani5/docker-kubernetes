⏺️ ➡️ 🟦 🔵🔹🔷 🔵 ☑️ ✔️ 🔴 ⭕ • ‣ → ⁕

# ⏺️ Reactjs/Spring Boot CI/CD and Deployment Flow

## ➡️ How your Spring Boot applications are deployed in AWS?

### 🟦 Using Non-Serverless 🔴

- Mostly used in real world applications

##### 🔵 Non-Serverless CI/CD Flow 🔴🔴🔴

```text
Developer
   ↓
GitHub / GitLab
   ↓
Webhook
   ↓
Jenkins (running on EC2)
   ↓
Build (Maven / Gradle)
   ↓
Docker Build(Create JAR file)
   ↓
Push Image to AWS ECR / Docker Hub
   ↓
Deploy to AWS EKS (kubectl / helm)
   ↓
EKS Cluster(Kubernetes Deployment)
   ↓
EC2 Worker Nodes
   ↓
Pods
   ↓
Spring Boot Microservices

```

- EKS is k8s cluster.
- EKS manages the Kubernetes control plane (master nodes).
- Inside EKS, worker nodes run on EC2 instances.
- There can be multiple worker nodes, so multiple EC2 instances are typically used to run the pods.
- **Scheduler** → decides which worker node should run the **Pod**.
- **Kubelet** (on the worker node) → pulls the Docker image from **ECR/DockerHub** and starts the container.

##### 🔵 Non-Serverless Infrastructure Runtime Flow 🔴🔴🔴

```text
Client / Browser
        │
        ▼
Route53 (DNS)
        │
        ▼
Application Load Balancer (ALB)
(Public Subnets)
        │
        ▼
Ingress Controller (inside EKS)
        │
        ▼
Kubernetes Service (ClusterIP)
        │
        ▼
Pods (Spring Boot Containers)
(Private Subnets)
        │
        ▼
RDS Database (PostgreSQL)
(Private Subnets)
```

### 🟦 Using Serverless

- In serverless, we don’t manage servers or containers. So Kuberntes is not used.
- The cloud provider manages the infrastructure automatically.

##### 🔵 Serverless CI/CD Flow

```text
Developer pushes code
        │
        ▼
GitHub / GitLab Repository
        │
        ▼
CI/CD Pipeline Triggered
(Jenkins / GitHub Actions / GitLab CI)
        │
        ▼
Build Spring Boot Application
        │
        ▼
Create JAR file
        │
        ▼
Package application for Lambda
(zip or container image)
        │
        ▼
Deploy to AWS Lambda
        │
        ▼
Update API Gateway configuration
```

##### 🔵 Serverless Infrastructure Runtime Flow

- Characteristics:
  - No server management
  - Auto scaling
  - Pay only for execution

```text
Client / Browser
        │
        ▼
API Gateway
        │
        ▼
Lambda Function
(Spring Boot logic)
        │
        ▼
Database
(DynamoDB / RDS)
```

## ➡️ How your Reactjs applications are deployed in AWS?

### 🟦 Using Serverless

##### 🔵 Serverless CI/CD Flow

```text
Developer pushes code
        │
        ▼
GitHub Repository
        │
        ▼
CI/CD Pipeline Triggered (Jenkins / GitHub Actions)
        │
        ▼
Install dependencies
        │
        ▼
Build React Application
        │
        ▼
Create build folder
        │
        ▼
Upload build files to S3 bucket
        │
        ▼
Invalidate CloudFront cache (optional)
```

- **CloudFront (CDN)**
  - Global caching
  - Faster delivery
  - HTTPS support
  - DDoS protection

##### 🔵 Serverless Infrastructure Runtime Flow

```text
User Browser
      │
      ▼
CloudFront (CDN)
      │
      ▼
S3 Bucket
      │
      ▼
React Static Files
```

- React runs on EC2.
- Nginx serves the static files.

```text
User Browser
      │
      ▼
CloudFront (optional CDN)
      │
      ▼
Load Balancer(ELB)
      │
      ▼
EC2 Instance
      │
      ▼
Nginx / Apache
      │
      ▼
React Static Files
```

### 🟦 Using Non-Serverless 🔴

- Mostly used in real world applications

##### 🔵 Non-Serverless CI/CD Flow

```text
Developer pushes code
        │
        ▼
GitHub Repository
        │
        ▼
CI/CD Pipeline Triggered (Jenkins / GitHub Actions)
        │
        ▼
Install dependencies
        │
        ▼
Build React Application
        │
        ▼
Create build folder
        │
        ▼
Copy build files to EC2
        │
        ▼
Replace old build files
        │
        ▼
Reload Nginx

```

##### 🔵 Non-Serverless Infrastructure Runtime Flow

```text
User Browser
      │
      ▼
CloudFront (optional CDN)
      │
      ▼
Load Balancer (ELB)
      │
      ▼
EC2 Instances
      │
      ▼
Nginx / Apache
      │
      ▼
React Static Files
```
