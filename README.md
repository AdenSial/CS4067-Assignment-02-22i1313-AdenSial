 Online Event Booking Platform 
This repository contains the extended version of the Online Event Booking Platform, originally developed in Assignment 01. In this assignment, the application has been containerized using Docker, orchestrated with Docker Compose, and deployed to Kubernetes using best DevOps practices.


📦 Objective
The primary objective of this assignment is to:

Dockerize each microservice of the Online Event Booking Platform.

Use Docker Compose to orchestrate and run the application locally.

Deploy all microservices to Kubernetes using appropriate YAML manifests.

Configure microservices using ConfigMaps and Secrets.

Expose services through a Kubernetes Ingress Controller.

🧱 Microservices Included
User Service

Event Service

Booking Service

Notification Service

Each microservice is containerized and configured to run independently, communicating over predefined network configurations.

📁 Project Structure
bash
Copy
Edit
/CS4067-Assignment-02-22i1313-AdenSial
│
├── user-service-codebase/
├── event-service-codebase/
├── booking-service-codebase/
├── notification-service-codebase/
├── frontend-service-codebase/
│
├── kubernetes/
│   ├── namespace.yaml
│   ├── configmap.yaml
│   ├── secrets.yaml
│   ├── deployment-service-user.yaml
│   ├── deployment-service-event.yaml
│   ├── deployment-service-booking.yaml
│   ├── deployment-service-notification.yaml
│   ├── deployment-service-frontend.yaml
│   └── ingress.yaml
│
├── docker-compose.yml
└── README.md
🐳 Dockerization
Each microservice contains its own Dockerfile which:

Uses minimal base images (e.g., python:3.12-slim, node:18-alpine)

Copies relevant code and dependencies

Specifies working directories and exposed ports

Defines appropriate CMD instructions

📝 Deliverable: Dockerfiles for all services are inside their respective folders.

📦 Docker Compose Setup
The docker-compose.yml file orchestrates:

All microservices

Databases (PostgreSQL, MongoDB)

Environment variables and networking

To run locally:

bash
Copy
Edit
docker-compose up --build
📝 Deliverable: docker-compose.yml

☸️ Kubernetes Deployment
Deployment and service YAMLs are provided for each microservice:

Each YAML file includes both Deployment and Service specifications

All microservices run in a custom namespace: OnlineEventBookingYourName

Ports, replicas, and environment variables are properly defined

📝 Deliverables:

namespace.yaml

deployment-service-*.yaml files (per microservice)

🔐 ConfigMaps & Secrets
Kubernetes manifests include:

configmap.yaml for environment variables and configurations

secrets.yaml for sensitive data (base64-encoded)

📝 Deliverables:

configmap.yaml

secrets.yaml

🌐 Ingress Configuration
An Ingress Controller routes traffic to the services:

Frontend is exposed as root

Backend APIs are accessible via subpaths (/api/users, /api/events, etc.)

Can be extended to support HTTPS with TLS

📝 Deliverable: ingress.yaml

🚀 How to Deploy on Kubernetes (Minikube or Cluster)
Start Minikube:

bash
Copy
Edit
minikube start
Apply the namespace:

bash
Copy
Edit
kubectl apply -f kubernetes/namespace.yaml
Apply ConfigMaps and Secrets:

bash
Copy
Edit
kubectl apply -f kubernetes/configmap.yaml
kubectl apply -f kubernetes/secrets.yaml
Apply deployments:

bash
Copy
Edit
kubectl apply -f kubernetes/deployment-service-user.yaml
kubectl apply -f kubernetes/deployment-service-event.yaml
kubectl apply -f kubernetes/deployment-service-booking.yaml
kubectl apply -f kubernetes/deployment-service-notification.yaml
kubectl apply -f kubernetes/deployment-service-frontend.yaml
Apply Ingress:

bash
Copy
Edit
kubectl apply -f kubernetes/ingress.yaml
