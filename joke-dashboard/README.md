# Multi-Container Dad Joke Dashboard

A production-ready multi-container application managed via Docker Compose that decouples data collection from data presentation. 

## 🏗️ Architecture Detail
* **Backend Worker (`updater`):** A lightweight background service built on Alpine Linux that dynamically fetches new jokes and populates a shared volume.
* **Frontend Web Server (`web`):** An Nginx instance that mounts the shared volume as a read-only data source to serve the live dashboard.

## 🔒 Security & Optimization Highlights
* **Alpine Package Efficiency:** Swapped standard Debian configurations for Alpine’s native package management (`apk add --no-cache`) to minimize attack surface and keep the image footprint ultra-slim.
* **Principle of Least Privilege:** Transitioned the runtime environment away from standard `root` access. Execution is restricted to an unprivileged custom `appuser`.
* **Runtime Validation:** Verified execution privileges via container inspectors:
  ```bash
  docker exec joke-dashboard-web-1 whoami
  # Output verified: nginx

🚀 Local Deployment
1, start the microservices:
```bash

docker compose up -d --build

Bind the remote port to your local environment for browser access:

```bash
ssh -L 8080:localhost:8080 user@<YOUR_SERVER_IP_ADDRESS>

Open http://localhost:8080 on your host machine.
