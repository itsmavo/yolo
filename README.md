# YOLO E-Commerce Project - Kubernetes (GKE) Deployment
## Overview
This repository contains the code and configuration files for deploying the YOLO E-Commerce application on Google Kubernetes Engine (GKE). The application is built using a microservices architecture, with separate services for the frontend, backend, and database.

- **Frontend**: The frontend service is built using React and communicates with the backend service via REST APIs.
- **Backend**: The backend service is built using Node.js and Express, and it interacts with the MongoDB database.
- **Database**: The database service uses MongoDB to store application data. Using a statefulset with persistent storage.

## Live Application URL
> **Link to the deployed application**: [YOLO E-Commerce](http://34.28.135.244:3000/)

## GKE Deployment
- **Namespace**: `default`
- **Services**:
  - **Frontend**: Exposed on port 3000 `LoadBalancer`
  - **Backend**: Exposed on port 5000 `LoadBalancer`
  - **Database**: Exposed on port 27017 `Headless Service`

## Concepts Applied
- **Kubernetes**: The application is deployed on GKE using Kubernetes, which provides container orchestration and management.
- **Docker**: The application is containerized using Docker, allowing for easy deployment and scaling.

| Feature | Description |
|---------|-------------|
| **StatefulSet** | Used for the MongoDB database to ensure data persistence. |
| **LoadBalancer** | Exposes the frontend and backend services to the internet. |
| **Persistent Volume** | Used for MongoDB to store data persistently. |
|**Resource Management** | Resource requests and limits are set for each service to ensure efficient resource utilization. |
|**Controllers** | Deployments and StatefulSets are used to manage the frontend and backend services, ensuring high availability, self healing and scalability. |

## Functionality
- Users can add items to their cart.
- MongoDB data is retained after pod restarts.
- Frontend and backend services are decoupled and communicate via REST APIs.
- Resource requests and limits are set for each service to ensure efficient resource utilization.

## Docker Images
- **Frontend**: `marvin0solo/marvin-yolo-client:v1.0.0`
- **Backend**: `marvin0solo/marvin-yolo-server:v1.0.0`
- **Database**: `mongo:latest`

# Author: Marvin Osolo

License: **[MIT](https://opensource.org/licenses/MIT)**