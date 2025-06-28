# Clients API DevOps Assessment

This repo contains the Kubernetes manifests and CI/CD setup for deploying a sample Clients API on Kubernetes using Jenkins, MongoDB, and TLS with Let's Encrypt.

## Components

- CI/CD with Jenkins (Jenkinsfile)
- Dockerized Clients API
- MongoDB as datastore
- Kubernetes manifests for:
  - Deployment & Service
  - Ingress with Let's Encrypt TLS
  - Cert Manager + ClusterIssuer + Certificate

## Domain

`clients.api.deltacapita.com` - Example FQDN with TLS support via Cert Manager

## CI/CD

Jenkinsfile in `/jenkins`:
- Checkout code
- Build Docker image
- Run tests
- Deploy to Kubernetes using `kubectl`

## Prerequisites

- Kubernetes Cluster with Ingress Controller installed
- Cert-Manager installed
- DockerHub or private registry for image push
- Jenkins with kubeconfig credentials

## Setup

- Deploy MongoDB and Clients API
```bash
kubectl apply -f k8s/
