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
