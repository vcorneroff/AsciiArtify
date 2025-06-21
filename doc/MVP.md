# MVP Deployment – AsciiArtify

## Infrastructure Overview

- **Kubernetes cluster**: k3d (local development)
- **GitOps**: ArgoCD configured to track the repository [go-demo-app](https://github.com/vcorneroff/go-demo-app)
- **Application Path**: `manifests/`
- **Branch**: `main`
- **Sync Policy**: Automatic (auto-sync)

## Deployment Process

1. Forked and cloned the [go-demo-app](https://github.com/den-vasyliev/go-demo-app) repository.
2. Created a Kubernetes cluster using k3d.
3. Installed ArgoCD into the cluster.
4. Configured ArgoCD to:
   - Track the application via Git.
   - Automatically deploy changes upon new commits.
5. Deployed the application successfully via ArgoCD and validated functionality in the browser.

## Automatic Synchronization

ArgoCD is configured to:
- Automatically sync changes from the Git repository.
- Self-heal the application state if discrepancies are detected.

This ensures continuous delivery and reliability of the deployment process.

## Video Demonstrations

### Application Functionality Demo

> A short demo showing the deployed application running on Kubernetes.

[![App Demo](https://img.youtube.com/vi/_LwPy3ROrZw/0.jpg)](https://youtu.be/_LwPy3ROrZw)

---

### 📹 ArgoCD Auto-Sync Demo

> Demonstrates auto-sync in ArgoCD after pushing a change to GitHub.

[![Sync Demo](https://img.youtube.com/vi/_LwPy3ROrZw/0.jpg)](https://youtu.be/_LwPy3ROrZw)

---

## Repository Structure
