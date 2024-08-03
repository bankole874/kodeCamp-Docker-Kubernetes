# Docker and Kubernetes 
## Build, Containerize, and Deploy a Simple Application

## Introduction
This project demonstrates a simple web application built with Flask, containerized using Docker, and deployed to a Kubernetes cluster. It also includes the use of Kubernetes ConfigMap and Secret for configuration management.

The application is a simple Flask web app that displays the message `"Hello, Welcome to KodeCamp DevOps Bootcamp!"`.

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
Build the Docker image:

```bash
docker build -t kocdapp:v2 .
```
![dockerBuild](https://github.com/user-attachments/assets/9ac4764e-c69d-431b-b5b4-7a6c0264d26a)

Run the Docker container:
```bash
docker run -p 5000:5000 kocdapp
```
![dockerRun](https://github.com/user-attachments/assets/25c93f68-8153-4cd5-adbd-edaf440bd3e2)

Tag and push the Docker image to Docker Hub:

```bash
docker tag kocdapp bankdoo/kc-docker-app:latest
docker push bankdoo/kodecamp-app:latest
```
![pushToDockerHub](https://github.com/user-attachments/assets/2059d5be-8da7-4381-bc74-662f7d24881e)

## Kubernetes Deployment
Start Minikube:

```bash
minikube start
```

Apply the ConfigMap, Secret, Deployment and Service:
```bash
kubectl apply -f kubernetes/configmap.yaml
kubectl apply -f kubernetes/secret.yaml
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml
```
![kubectlapply](https://github.com/user-attachments/assets/bc7a22c5-5c40-44ab-8946-0a1ba7a29852)