# Concept: Local Kubernetes Deployment for PoC "AsciiArtify"

## Introduction

To enable local Proof of Concept (PoC) development for the "AsciiArtify" project — a machine-learning powered image-to-ascii-art converter — we evaluated three popular Kubernetes-based solutions:

- **minikube** — a classic local Kubernetes tool with virtualization options.
- **kind** (Kubernetes IN Docker) — spins up Kubernetes clusters in Docker containers.
- **k3d** — a lightweight Kubernetes distribution (k3s) running in Docker containers via Rancher.

## Characteristics

| Feature                        | minikube                     | kind                          | k3d                             |
|-------------------------------|------------------------------|-------------------------------|----------------------------------|
| OS Support                    | Linux, macOS, Windows        | Linux, macOS, Windows         | Linux, macOS, Windows            |
| Architecture Support          | amd64, arm64                 | amd64, arm64                  | amd64, arm64                     |
| Resource Requirements         | Moderate                     | Low                           | Very Low                         |
| Startup Speed                 | Medium                       | Fast                          | Very Fast                        |
| Docker Dependency             | Optional (can use Podman)    | Required                      | Required                         |
| Podman Compatibility          | Yes (relatively stable)      | No                            | Limited                          |
| CI/CD Automation              | Limited                      | Good                          | Excellent                        |
| UI Dashboard                  | Built-in                     | None                          | None                             |
| Monitoring                    | Manual setup                 | Requires setup                | Requires setup                   |
| Ease of Setup                 | High                         | Medium                        | High                             |
| Docs & Community              | Mature & broad               | Active                        | Rapidly growing                  |

## Pros & Cons

### **minikube**
**Pros:**
- Simple setup with a GUI dashboard.
- Supports multiple drivers (Docker, Podman, VirtualBox).

**Cons:**
- Slower to start.
- Limited CI/CD integration.
- Heavier resource usage.

### **kind**
**Pros:**
- Lightweight and fast.
- Ideal for CI pipelines and testing.
- Multi-node clusters supported.

**Cons:**
- No Podman support.
- No GUI.
- Less intuitive for manual use.

### **k3d**
**Pros:**
- Fastest and lightest option.
- Built on k3s (lightweight Kubernetes).
- Great for PoC and CI/CD.

**Cons:**
- Less beginner-friendly.
- Relies heavily on Docker.

## Demo

> PoC repository:  
> **https://github.com/<username>/AsciiArtify**

### Quickstart Hello World with k3d

```bash
# 1. Create a cluster
k3d cluster create asciiartify

# 2. Verify cluster is running
kubectl get nodes

# 3. Deploy Hello World app
kubectl apply -f manifests/hello.yaml

# 4. Get service endpoint
kubectl get svc hello
```

📝 Demo YAML: [`hello.yaml`](https://github.com/vcorneroff/AsciiArtify/blob/main/hello.yaml)

## Conclusions & Recommendations

### We recommend **`k3d`** as the best tool for local Kubernetes development for AsciiArtify PoC:

- Fastest deployment.
- Lightweight and CI/CD ready.
- Easy multi-node setups.

**minikube** is a good alternative for UI-based users or when Docker is unavailable.

**kind** is more suitable for automated testing pipelines.

> ✅ We selected **k3d** for initial PoC deployment and will integrate GitHub Actions for future CI/CD workflows.

## Demo
![K3d Demo](./demo.gif)
---

*Document prepared by AsciiArtify engineering team for Kubernetes PoC environment selection.*
