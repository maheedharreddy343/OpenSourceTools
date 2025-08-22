# Introduction to DevOps and Docker

## DevOps Overview

DevOps is a set of practices that combines software development (Dev) and IT operations (Ops) to shorten the systems development life cycle and provide continuous delivery with high software quality. Key principles include:

- **Collaboration**: Breaking down silos between development and operations teams
- **Automation**: Automating repetitive tasks to improve efficiency
- **Continuous Integration/Continuous Delivery (CI/CD)**: Automating testing and deployment
- **Infrastructure as Code (IaC)**: Managing infrastructure through code
- **Monitoring and Logging**: Continuous feedback loops for improvement

## Docker Introduction

### What is Docker?

Docker is an open-source platform that uses OS-level virtualization to deliver software in packages called **containers**. Containers bundle an application with all its dependencies, libraries, and configuration files.

### How Docker Works

Docker uses a client-server architecture:

1. **Docker Client**: Command-line interface (CLI) for interacting with Docker
2. **Docker Daemon**: Background service that manages containers, images, networks, and storage
3. **Docker Registry**: Stores Docker images (e.g., Docker Hub)

Key components:

- **Images**: Read-only templates used to create containers (built from Dockerfiles)
- **Containers**: Runnable instances of an image
- **Dockerfile**: Text file with instructions to build an image
- **Volumes**: Persistent storage for containers

### Importance of Docker

- **Consistency**: Eliminates "works on my machine" issues
- **Portability**: Run anywhere (laptop, cloud, on-premises)
- **Efficiency**: Lightweight containers share host OS kernel
- **Scalability**: Easy horizontal scaling with orchestration tools
- **Isolation**: Processes run in isolated environments
- **Version Control**: Image versioning and rollbacks

### Why Use Docker?

- **Rapid Deployment**: Spin up environments in seconds
- **Microservices**: Ideal for microservice architectures
- **CI/CD Integration**: Streamlines build-test-deploy pipelines
- **Resource Efficiency**: Lower overhead than traditional VMs
- **Dev-Prod Parity**: Identical environments across all stages

### Core Concept

Docker packages applications and dependencies into standardized units called **containers** that:

- Share the host OS kernel (unlike VMs)
- Run isolated processes
- Include all runtime requirements
- Can be versioned, distributed, and run consistently anywhere

---

## Virtualization vs. Containerization

| **Feature**           | **Virtualization (VMs)**      | **Containerization (Docker)** |
| --------------------------- | ----------------------------------- | ----------------------------------- |
| **Architecture**      | Full OS virtualization (hypervisor) | OS-level virtualization             |
| **Resource Overhead** | Heavy (full OS per VM)              | Lightweight (shared kernel)         |
| **Startup Time**      | Minutes                             | Seconds                             |
| **Performance**       | Near-native but with overhead       | Near-native with minimal overhead   |
| **Isolation**         | Strong (hardware-level)             | Moderate (process-level)            |
| **Density**           | Low (few VMs per host)              | High (100s of containers per host)  |
| **Use Cases**         | Legacy apps, strong isolation needs | Microservices, cloud-native apps    |

---

## Docker Basics: Building and Running Containers

### 1. Building Images with Dockerfile

```dockerfile
# Example Dockerfile
FROM python:3.9-slim          # Base image
WORKDIR /app                  # Set working directory
COPY requirements.txt .       # Copy dependencies
RUN pip install -r requirements.txt  # Install packages
COPY . .                      # Copy application code
EXPOSE 5000                   # Expose port
CMD ["python", "app.py"]      # Default command
```

Build the image:

```bash
docker build -t myapp:1.0 .
```

### 2. Running Containers

```bash
# Basic container run
docker run -d -p 8080:5000 --name myapp-container myapp:1.0

# Interactive container
docker run -it ubuntu:22.04 /bin/bash

# Mount volumes
docker run -v /host/path:/container/path myapp:1.0
```

### 3. Managing Containers

```bash
docker ps          # List running containers
docker stop <id>   # Stop container
docker start <id>  # Start stopped container
docker rm <id>     # Remove container
docker images      # List images
docker rmi <image> # Remove image
```

---

## Docker Compose: Multi-Container Applications

### What is Docker Compose?

Tool for defining and running multi-container Docker applications using YAML files.

### Key Features

- Define services, networks, and volumes in `docker-compose.yml`
- Single command to start/stop all services
- Manage application lifecycle

### Example docker-compose.yml

```yaml
version: '3.8'
services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumes:
      - .:/app
    depends_on:
      - redis
  
  redis:
    image: "redis:alpine"
    ports:
      - "6379:6379"

networks:
  default:
    driver: bridge
```

### Common Commands

```bash
docker-compose up -d          # Start all services
docker-compose down            # Stop and remove containers
docker-compose logs            # View logs
docker-compose exec web bash   # Execute command in service
```

### Networking

- Containers on the same network can communicate using service names
- Default network created automatically
- Custom networks can be defined:
  ```yaml
  networks:
    frontend:
    backend:
  ```

---

## Docker Hardening: Security Best Practices

### 1. Image Security

- **Use Official Base Images**: From trusted sources (Docker Hub, ECR, etc.)
- **Minimal Base Images**: `alpine`, `slim` variants reduce attack surface
- **Regular Updates**: Patch base images frequently
- **Scan Images**: Use tools like:

  ```bash
  docker scan myapp:1.0
  ```

  or third-party tools (Trivy, Clair, Snyk)

### 2. Container Runtime Security

- **Run as Non-Root User**:
  ```dockerfile
  RUN addgroup -g 1001 appgroup && \
      adduser -u 1001 -G appgroup -s /bin/sh -D appuser
  USER appuser
  ```
- **Read-Only Filesystems**:
  ```bash
  docker run --read-only myapp:1.0
  ```
- **Resource Limits**:
  ```bash
  docker run --memory=512m --cpus=1.0 myapp:1.0
  ```
- **Seccomp/AppArmor Profiles**: Restrict system calls

### 3. Network Security

- **Private Networks**: Isolate containers in custom networks
- **Firewall Rules**: Use host firewalls (iptables) to restrict access
- **Encrypted Communication**: TLS for container-to-container traffic

### 4. Secrets Management

- **Docker Secrets** (Swarm mode):
  ```bash
  echo "my_secret" | docker secret create db_password -
  ```
- **Environment Variables**: Avoid storing secrets in images
- **External Tools**: HashiCorp Vault, AWS Secrets Manager

### 5. Host Security

- **Docker Daemon Security**:
  - Expose daemon over TLS only
  - Use user namespaces
- **Kernel Hardening**: Enable security modules (SELinux, AppArmor)
- **Regular Audits**: Monitor container activity and access logs

### 6. Best Practices Checklist

- [ ] Scan images for vulnerabilities
- [ ] Use minimal base images
- [ ] Run containers as non-root users
- [ ] Implement resource limits
- [ ] Isolate containers with networks
- [ ] Encrypt sensitive data at rest and in transit
- [ ] Regularly update Docker engine and host OS
- [ ] Implement least privilege access controls
- [ ] Monitor container activity and logs
- [ ] Use trusted registries with image signing

---
