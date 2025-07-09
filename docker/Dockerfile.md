# Dockerfile  

    /* 1. Use an official base image
    FROM openjdk:17
    
    /* 2. Set the working directory inside the container
    WORKDIR /app
    
    /* 3. Copy compiled Java class (or your JAR) into the container
    COPY Hello.class .
    
    /* 4. Run the application using Java
    CMD ["java", "Hello"]

### Meaning Of Each Line Of Instruction:
| Line                    | Explanation                                                      |
| ----------------------- | ---------------------------------------------------------------- |
| `FROM openjdk:17`       | Uses OpenJDK 17 as the base image (includes Java).               |
| `WORKDIR /app`          | Sets the working directory inside the container to `/app`.       |
| `COPY Hello.class .`    | Copies the compiled Java class from local to container's `/app`. |
| `CMD ["java", "Hello"]` | Runs `java Hello` when the container starts.                     |


# Commands
| #  | Command                               | Explanation                                                                                |
| -- | ------------------------------------- | ------------------------------------------------------------------------------------------ |
| 1  | `docker build -t myapp .`             | Builds a Docker image from the Dockerfile in the current directory and tags it as `myapp`. |
| 2  | `docker images`                       | Lists all locally stored Docker images.                                                    |
| 3  | `docker run myapp`                    | Runs a container from the `myapp` image.                                                   |
| 4  | `docker ps`                           | Lists currently running containers.                                                        |
| 5  | `docker ps -a`                        | Lists all containers (including stopped ones).                                             |
| 6  | `docker stop <container_id>`          | Gracefully stops a running container.                                                      |
| 7  | `docker rm <container_id>`            | Deletes a stopped container.                                                               |
| 8  | `docker rmi <image_id>`               | Removes a Docker image from local storage.                                                 |
| 9  | `docker exec -it <container_id> bash` | Opens an interactive terminal inside a running container.                                  |
| 10 | `docker logs <container_id>`          | Displays logs from the specified container.                                                |
| 11 | `docker pull <image_name>`            | Pulls an image from Docker Hub (e.g., `docker pull nginx`).                                |
| 12 | `docker push <image_name>`            | Pushes your image to Docker Hub (must be logged in).                                       |
| 13 | `docker login`                        | Logs into your Docker Hub account.                                                         |
| 14 | `docker network ls`                   | Lists all Docker networks.                                                                 |
| 15 | `docker volume ls`                    | Lists all Docker volumes.                                                                  |
