# Dcoker
### 🔹 1) Image
     A Docker image is a lightweight, standalone, and executable package that includes everything needed to run 
     a piece of software: code, runtime, libraries, environment variables, and config files.
     Think of it like a template used to create containers.
### 🔹 2) Container
    A Docker container is a running instance of a Docker image. It is isolated, lightweight, and portable.
    It’s like running a program using the template (image).
### 🔹 3) Volumes
     Volumes are used to persist data in Docker. Even if a container is deleted, data in a volume remains intact.
     Useful for databases or saving logs.

### 🔹 4) Compose
       Docker Compose is a tool used to define and run multi-container Docker applications using a YAML file 
        (docker-compose.yml).
       You can run frontend, backend, and database containers together using one command.

### 🔹 5) Docker Hub
       Docker Hub is a cloud-based registry where you can find and share container images. You can push your custom
       images and pull official ones like mysql, node, openjdk, etc.


### Dcokerfile
    /* Use OpenJDK as the base image
    FROM openjdk:17
    
    /* Set the working directory inside the container
    WORKDIR /app
    
    /* Copy compiled Java class to the container
    COPY Hello.class .
    
    /* Command to run the Java class
    CMD ["java", "Hello"]
