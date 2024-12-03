# Cosmocloud DevOps Intern Helm Chart Submission

## Project Overview
Kubernetes deployment for a three-service application using Helm:
- Backend Service
- Frontend Service
- Redis Database

## Deployment Specifications
- Namespace: `default`
- Replicas: 1 per service
- Services:
  * Backend: ClusterIP (Port 8000)
  * Frontend: NodePort (Port 5175, NodePort 31000)
  * Redis: ClusterIP (Port 6379)

## Prerequisites
- Kubernetes Cluster
- Helm
- kubectl

## Installation
```bash
helm install testapp cosmocloud-deploy
```

## Service Communication
- Backend connects to Redis via `redis://redis-svc:6379`
- Frontend connects to Backend via `http://backend-svc:8000`

## Access
Frontend accessible via NodePort: `localhost:31000`

## Images
- Backend: `shreybatra/sample-backend`
- Frontend: `shreybatra/sample-frontend`
- Database: `redis`
