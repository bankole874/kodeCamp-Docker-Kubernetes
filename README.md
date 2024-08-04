# Docker and Kubernetes 
## Build, Containerize, and Deploy a Simple Application

## Introduction
This project demonstrates a simple web application built with Flask, containerized using Docker, and deployed to a Kubernetes cluster. It also includes the use of Kubernetes ConfigMap and Secret for configuration management.

## Table of Contents
- Project Overview
- Prerequisites
- Application Structure
- Docker Instructions
- Kubernetes Deployment
- Testing the Deployment
- Bonus: Using ConfigMap and Secret
- Issues Encountered
- Docker Hub Image
- Project Overview

## Project Overview
The application is a simple Flask web app that displays the message `"Hello, Welcome to KodeCamp DevOps Bootcamp!"`.

## Prerequisites
Python 3.9, Docker, Docker Hub account, Minikube, kubectl

## Application Structure
```bash
kodecamp-Task07
├── app
│   ├── __init__.py
│   ├── app.py
│   └── requirements.txt
├── kubernetes
│   ├── configmap.yaml
│   ├── deployment.yaml
│   ├── secret.yaml
│   └── service.yaml
├── Dockerfile
├── README.md
└── .gitignore
```

## Docker Instructions
- Build the Docker image:

```bash
docker build -t kocdapp:v2 .
```
![dockerBuild](https://github.com/user-attachments/assets/9ac4764e-c69d-431b-b5b4-7a6c0264d26a)

- Run the Docker container:
```bash
docker run -p 5000:5000 kocdapp
```
![dockerRun](https://github.com/user-attachments/assets/25c93f68-8153-4cd5-adbd-edaf440bd3e2)

- Tag and push the Docker image to Docker Hub:

```bash
docker tag kocdapp bankdoo/kc-docker-app:latest
docker push bankdoo/kodecamp-app:latest
```
![pushToDockerHub](https://github.com/user-attachments/assets/2059d5be-8da7-4381-bc74-662f7d24881e)

## Kubernetes Deployment
- Start Minikube:

```bash
minikube start
```

- Apply the Deployment and Service:
```bash
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml
```

## Testing the Deployment

- Port-forward to access the application locally and access the application from browser:
```bash
kubectl port-forward service/kodecamp-app-service 8080:80
```

![portForwarding](https://github.com/user-attachments/assets/cf8ea4bc-9287-478b-a515-aa180bf2bdd8)

## Bonus: Using ConfigMap and Secret
- Create a ConfigMap
- Create a Secret
- Updated the application to use environment variables
- Update the Kubernetes Deployment to use ConfigMap and Secret
![updated_bonus](https://github.com/user-attachments/assets/cfea9898-ee99-4b6c-b23e-63c0e79945fc)
- Apply the updated Deployment
```bash
kubectl apply -f kubernetes/configmap.yaml
kubectl apply -f kubernetes/secret.yaml
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml
```
![kubectlapply](https://github.com/user-attachments/assets/bc7a22c5-5c40-44ab-8946-0a1ba7a29852)

- Check for the configurations in one of the pods.
![kubectl_exec](https://github.com/user-attachments/assets/bf277bbc-467c-42fd-8690-096868fcd05d)

## Issues Encountered
- Ensuring Flask uses the latest version for compatibility.
![flaskUpgradeError](https://github.com/user-attachments/assets/86421a6f-a8e3-40eb-b854-bb638dd65fd0)
- Ensuring Flask runs on 0.0.0.0 instead of localhost.
- Correctly tagging and pushing the Docker image to Docker Hub.
- Debugging Kubernetes configurations to ensure the correct deployment.


## Docker Hub Image
![dockerHub](https://github.com/user-attachments/assets/4f6ffe8e-3310-4dc8-9c79-a6df5304d170)

[Link to Docker Hub Image](https://hub.docker.com/layers/bankdoo/kc-docker-app/latest/images/sha256:2f840a36ae30fdcfe2916b87efd2fe22e2e443a6f83f9d24bc863f540f1124d7?uuid=EB277BB6-E406-4BF5-920F-688A814085E3)

## Project Overview
This README provides an overview of the project, setup instructions, and detailed steps for Dockerizing and deploying the application to a Kubernetes cluster, including the bonus tasks of using ConfigMap and Secret.
