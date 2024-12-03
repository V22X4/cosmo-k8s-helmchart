# Cosmocloud Deploy Helm Chart

## Overview
This Helm chart deploys a complete application stack consisting of:
- Backend Service
- Frontend Service
- Redis Database

## Deployment Details
- Namespace: `default`
- Backend: 
  - Image: `shreybatra/sample-backend`
  - Service Type: ClusterIP
  - Port: 8000
  - Environment: `REDIS_URI=redis://redis-svc:6379`

- Frontend:
  - Image: `shreybatra/sample-frontend`
  - Service Type: NodePort
  - Port: 5175
  - NodePort: 31000
  - Environment: `BACKEND_URL=http://backend-svc:8000`

- Redis:
  - Image: `redis`
  - Service Type: ClusterIP
  - Port: 6379

## Deployment Instructions
```bash
helm install testapp cosmocloud-deploy --atomic --timeout 30s
```

## Notes
- Each service is deployed with 1 replica
- Services are configured to communicate with each other via internal Kubernetes DNS
- Environment variables are set to enable proper inter-service communication