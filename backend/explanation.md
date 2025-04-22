# Docker Containerisation and Orchestration Explanation
Project to create docker containers and automate the deployment process for managing containers through docker-compose.yml,docker networking and working with docker volumes.

### Web Application:
I selected `node:16-alpine` as the base image for the web application. This image was chosen because:
- It is lightweight and reduces the overall image size, ensuring the final image remains under 400MB.
- It includes all the necessary tools for running a Node.js application without unnecessary extras.

### MongoDB:
I used the official `mongo:5.0` image from DockerHub. This choice ensures compatibility with modern MongoDB features while providing a stable and secure environment.
- The image is well-maintained and regularly updated, ensuring security and performance.

## **Dockerfile Directives**
1. **FROM**: Specifies the base image.
2. **WORKDIR**: Sets the working directory for subsequent instructions.
3. **COPY**: Copies files from the host to the container.
4. **RUN**: Executes commands to install dependencies.
5. **EXPOSE**: Opens port 3000 for external access.
6. **CMD**: Defines the default command to start the application.

## **Docker-Compose Networking**

The `docker-compose.yaml` file defines a custom bridge network called `app-network`. This allows the `web` and `mongo` containers to communicate seamlessly. Here is the relevant section:

```yaml
networks:
  app-network:
```

Each service is attached to this network to ensure proper communication. The web application can connect to the MongoDB service using the hostname `mongo` within the network.

---

## **Volume Definition and Usage**

Volumes ensure data persistence for the MongoDB container, even if the container is restarted or rebuilt. The following configuration in `docker-compose.yaml` creates a named volume:

```yaml
volumes:
  mongo-data:
```

This volume is mounted to the MongoDB container:

```yaml
mongo:
  volumes:
    - mongo-data:/data/db
```

This setup ensures that product data added through the application remains intact.

---
## **Good Practices**

### Image Tagging:
- All images were tagged using semantic versioning (e.g., `web:1.0`, `mongo:5.0`).

### Naming Conventions:
- Containers and images were given descriptive names for easy identification.

### Lightweight Images:
- Chose minimal base images to reduce the total image size below 400MB.

---