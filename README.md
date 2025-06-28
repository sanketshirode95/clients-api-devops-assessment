# Clients API - DevOps Assessment

This project sets up a full CI/CD pipeline using Jenkins and Kubernetes for the Clients API.

## Features

- CI/CD with Jenkins
- Kubernetes deployment
- MongoDB as datastore
- NGINX Ingress + Let's Encrypt TLS
- Live URL: `https://clients.api.deltacapita.com`

## Folder Structure

- `Jenkinsfile`: Pipeline definition
- `k8s/`: Kubernetes manifests
- `Dockerfile`: API container build

## How to Deploy

```bash
kubectl apply -f k8s/issuer.yaml
kubectl apply -f k8s/
