# Sakura - Deployment scripts for Sayonika

This contains the production Sayonika scripts for Sayonika, these are applied sequentially, and should not be applied in any way at the same time.


## Requirements

- Kubernetes 1.13 and above
- A cluster of at least 3 nodes (1 master, 2 workers).
- Master with Nginx Ingress Provider.

## Deploying

Simply refer to `manifests/`. You should deploy the following IN ORDER:

- Prerequisites
  - ElasticSearch
  - PostgreSQL

- Backend (1st deploy)
  - Do not expose this to the internet! Frontend will handle the proxying.

- Frontend (2nd and final deploy)
  - Deploy Ingress at any host (by default at `sayonika.local`).

