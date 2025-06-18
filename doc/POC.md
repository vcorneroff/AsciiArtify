# Proof of Concept: ArgoCD Deployment for AsciiArtify

## Overview

This Proof of Concept (PoC) demonstrates the technical feasibility of using ArgoCD as a GitOps solution for the AsciiArtify project. It includes a minimal but functional deployment of ArgoCD on a local Kubernetes cluster, using k3d as the container-based Kubernetes provider.

## Objectives

- Deploy a local Kubernetes cluster using k3d
- Install and configure ArgoCD
- Access ArgoCD Web UI
- Demonstrate GitOps-based deployment capability

## Prerequisites

Make sure the following tools are installed:

- [Docker](https://www.docker.com/)
- [k3d](https://k3d.io/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [ArgoCD CLI (optional)](https://argo-cd.readthedocs.io/en/stable/cli_installation/)

## Step-by-Step Setup

### 1. Create a Kubernetes cluster with k3d

```bash
k3d cluster create asciiartify
```

You can verify the cluster is working:

```bash
kubectl get nodes
```

### 2. Install ArgoCD in the cluster

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Wait a few moments for the ArgoCD pods to be ready:

```bash
kubectl get pods -n argocd
```

### 3. Port-forward ArgoCD UI to your local machine

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

Then open [https://localhost:8080](https://localhost:8080) in your browser.

> Note: You may need to accept a self-signed SSL certificate warning.

### 4. Get the default admin password

```bash
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d
```

Use:
- **Username**: `admin`
- **Password**: (output from command above)

### 5. Optional: Install and login via ArgoCD CLI

Install ArgoCD CLI:

```bash
brew install argocd # macOS
```

Login:

```bash
argocd login localhost:8080 --username admin --password <your-password> --insecure
```

## Example ArgoCD Application (optional)

You may define an example application in YAML (e.g., `manifests/app.yaml`) pointing to a public Git repo to test GitOps flows.

Documentation:
- [ArgoCD Application Spec](https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/)

## Outcome

If all steps are completed successfully, the team will have access to a working ArgoCD instance with Web UI and CLI. This environment will serve as the foundation for GitOps-based deployments of AsciiArtify MVP.

## References

- https://argo-cd.readthedocs.io/en/stable/
- https://k3d.io/
- https://kubernetes.io/docs/home/
