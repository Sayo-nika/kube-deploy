# Sakura - Deployment scripts for Sayonika

This contains the production Sayonika scripts for Sayonika, these are applied sequentially, and should not be applied in any way at the same time.


## Requirements

- Kubernetes 1.13 and above, K3s works as well.
- A cluster of at least 3 nodes (1 master, 2 workers).
- A running PostgreSQL Database.
- Docker (for Compose/Swarm).

## Deploying

Simply refer to the YMLs You should do the following IN ORDER:

- Prerequisites
  - PostgreSQL

- Edited the Secrets part
   - We use default `postgres` in `SAYONIKA_DB_HOST` and `5432` in `SAYONIKA_DB_PORT`. This is meant if you deployed with a PostgreSQL server within Kubernetes. If you don't wish to, edit them to their respective URLs.

- Backend (1st deploy)
  - Do not expose this! Frontend will handle the proxying (by default the configuration will just expose it within the cluster).

- Frontend (2nd and final deploy)
  - Its exposed as a NodePort, so you can use it with your existing reverse proxy (Sayonika Production uses K3s as well so Ingresses aren't supported).

For compose, just edit `docker-compose.yml` and run it as usual.
