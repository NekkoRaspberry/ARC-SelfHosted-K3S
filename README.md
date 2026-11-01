![Auto Assign](https://github.com/NekkoRaspberry/demo-repository/actions/workflows/auto-assign.yml/badge.svg)

![Proof HTML](https://github.com/NekkoRaspberry/demo-repository/actions/workflows/proof-html.yml/badge.svg)


# ARC-SelfHosted-K3S

A self-hosted GitHub Actions runner running on a Raspberry Pi 4, managed by K3s and Actions Runner Controller (ARC).

## Architecture

- **Hardware:** Raspberry Pi 4 (8 GB RAM)
- **OS:** Raspberry Pi OS Lite 64-bit
- **Kubernetes:** K3s
- **Container runtime:** containerd
- **CI/CD:** GitHub Actions
- **Runner management:** Actions Runner Controller
- **Package manager:** Helm

## Components

| Component | Purpose |
|---|---|
| K3s | Lightweight Kubernetes cluster |
| Helm | Kubernetes package management |
| Portainer | Kubernetes graphical management |
| ARC | Manages self-hosted GitHub Actions runners |

## ARC Configuration

- GitHub Organization: `NekkoRaspberry`
- Runner scale set: `nekko-runners`
- Controller namespace: `arc-systems`
- Runner namespace: `arc-runners`


## Test

Workflow: `.github/workflows/arc-test.yml`

The test workflow verifies that:
- GitHub Actions can request a runner.
- ARC creates a runner on the Raspberry Pi.
- The runner executes commands successfully.
- The runner uses ARM64 architecture.

**Result:** Successful execution on the Raspberry Pi.

## Useful Commands

Check Kubernetes nodes:

```bash
kubectl get nodes
```

Check ARC components:

```bash
kubectl get pods -n arc-systems
```

Check runner pods:

```bash
kubectl get pods -n arc-runners
```

Check Helm releases:

```bash
helm list -A
```

## Roadmap

- [x] Install K3s
- [x] Install Helm
- [x] Deploy Portainer
- [x] Install ARC
- [x] Configure GitHub App authentication
- [x] Test self-hosted runner
- [ ] Build and publish container images to GHCR
- [ ] Automate deployments to K3s
- [ ] Implement production deployment permissions

## Goal

Build a self-hosted CI/CD platform using GitHub Actions, ARC and K3s, with automated application deployment to the Raspberry Pi.