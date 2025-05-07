# IP3 Explanation (Docker containerization and deployment of a full-stack YOLO application)
Project to create docker containers and automate the deployment of a full-stack application using docker-compose, docker networking, docker volumes, ansible and Vagrant. 

## Pre-requisites
- Github account
- Dockerhub account
- Vagrant
- Ansible
- MongoDB account(for database application)
- Docker Volumes
- Container Networking
- Docker Orchestration

## Explanation of the project
Step 1: Forking and cloning the repository
```bash
git clone https://github.com/itsmavo/yolo
```
Step 2: Creating a Dockerfile and choosing a base image
The main factor to consider when choosing a base image is the size of the image. The smaller the image, the faster it will be to build and deploy. In this case, we chose the `node-16:alpine` image as our base image because it is a lightweight image that is optimized for running Node.js applications.  
```dockerfile
FROM node:16-alpine
```
use multistage build to reduce the size of the final image
```sh
touch .dockerignore
```
Step 3: Creating a Dockerfile for the frontend, backend and database

```dockerfile
# Dockerfile for frontend and Backend
FROM node:16-alpine AS build
```
Connecting to the MongoDB database
```sh
let dbName = process.env.DB_NAME;(Good practice to use environment variables)
```
Creating docker-compose.yaml file to orchestrate the containers

Client image to run the frontend  and server image for versioning
```sh
image: marvin0solo/marvin-yolo-client:v1.0.0
```

Backend image to run the backend
```sh
image: marvin0solo/marvin-yolo-backend:v1.0.1
```

MongoDB image to run the database
```sh
image: mongo
```

Step 4: Build locally and push to Dockerhub
```sh
docker build -t marvin0solo/marvin-yolo-client:v1.0.0 .

docker build -t marvin0solo/marvin-yolo-backend:v1.0.1 .

docker run -p 3000:3000 marvin0solo/marvin-yolo-client:v1.0.0

docker run -p 5000:5000 marvin0solo/marvin-yolo-backend:v1.0.1

docker push marvin0solo/marvin-yolo-client:v1.0.0

docker push marvin0solo/marvin-yolo-backend:v1.0.1
```
Pull the images from Dockerhub 
```sh
docker compose up
```
Step 5: Docker compose to create a network and volumes
Network to connect the containers

```bash
docker create network 
subnet: 172.20.0.0/16
```
Volumes to persist data
```yaml
volumes:
  app-mongo-data:
    driver: local
```

Step 6: Creating a Vagrantfile
```sh
vagrant up
```
Step 7: Creating an Ansible playbook
```sh
touch ansible.cfg
touch playbook.yml
```