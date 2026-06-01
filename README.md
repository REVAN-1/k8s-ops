# k8s-ops

My Homelab Kubernetes repository for a Talos cluster on Proxmox, managed via GitOps with FluxCD.

## Overview

This (mirrored) repository contains the Kubernetes and infrastructure definitions for my home lab setup. It's not really “best practice,” but it's worked so far. 

### Stack

- **Kubernetes OS:** Talos
- **Hypervisor:** Proxmox
- **GitOps:** FluxCD
- **CI / Automation:** Woodpecker
- **Dependency Updates:** Renovate

## Architecture

The cluster runs as a Talos-based Kubernetes cluster on Proxmox.  
Deployments and configurations are rolled out declaratively via FluxCD from this repository.

In addition, the cluster uses several external services that are not run directly within Kubernetes.

### External / Non-K8s Services

- **Technitium DNS** as an internal DNS server
- **Garage S3** for backups
- **VyOS** as a router and BGP peer
- **Cephadm-Cluster** for app storage
- **NAS / NFS** for bulk storage

### External dependencies

- DynDNS
- DNS-Provider (e.g. Hetzner or Cloudflare)

## Repository Structure

```text
.
├── clusters/
│   └── talos-pve/
│       ├── apps/              # User/Application Workloads
│       ├── infrastructure/    # Core Services and Platform Components
│       ├── flux-system/       # Flux Bootstrap and Customizations
│       └── sources/           # Helm repositories and other sources
├── talhelper/                 # Talos Cluster Configuration
└── renovate.json              # Renovate Configuration