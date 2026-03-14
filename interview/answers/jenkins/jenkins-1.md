⏺️ ➡️ 🟦 🔵 🟢 🔴 ⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️ Jenkins Pipeline Configuration Flow (Complete CI/CD)

```text
Developer
   ↓
Git Push
   ↓
Webhook Trigger
   ↓
Jenkins Pipeline Start
   ↓
Checkout Code
   ↓
Build (Maven / Gradle)
   ↓
Run Tests
   ↓
Code Quality Scan (SonarQube)
   ↓
Build Docker Image
   ↓
Push Image to Registry
   ↓
Deploy to Kubernetes
   ↓
Application Live
```

### ➡️ Developer Pushes Code

```cmd
git add .
git commit -m "new feature"
git push origin main
```

### ➡️ Webhook Triggers Jenkins

- The Git repository sends a **webhook** notification to Jenkins.
- So Jenkins automatically starts the pipeline.

```text
Git Repository
      ↓
Webhook Trigger
      ↓
Jenkins Pipeline Starts
```

### ➡️ Jenkins Pulls Source Code

- Jenkins pulls the latest code from Git

```cmd
Jenkins → Git Clone
```

```java
stage('Checkout Code'){
git 'https://github.com/project/repo.git'
}
```

### ➡️ Build Application

```cmd
mvn clean install
```

- Output

```text
JAR / WAR file generated
target/app.jar
```

### ➡️ Run Unit Tests

```cmd
mvn test
```

- If tests fail → pipeline stops

### ➡️ Static Code Analysis (Optional but Mostly used in real world)

- SonarQube

```cmd
Jenkins → SonarQube Scan
```

### ➡️ Build Docker Image

- After build success, Jenkins creates a Docker image.

```cmd
docker build -t myapp:v1 .
```

```yml
FROM openjdk:17
COPY target/app.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```

### ➡️ Push Image to Docker Registry

- The Docker image is pushed to a registry(DockerHub, AWS ECR)

```yml
docker push myrepo/myapp:v1
```

### ➡️ Deploy to Kubernetes

- Now Jenkins deploys the application to Kubernetes cluster.

```yml
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

```text
Kubernetes Cluster
       ↓
Deployment
       ↓
Pods
       ↓
Service
       ↓
Load Balancer
```

### ➡️ Application Running

```cmd
User
 ↓
Load Balancer / Ingress
 ↓
Kubernetes Service
 ↓
Pods (Spring Boot Containers)
 ↓
Docker Container
 ↓
Spring Boot Application
```
