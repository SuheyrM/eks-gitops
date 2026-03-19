## EKS-GitOpa

This repository contains Kubernetes manifests and Helm-based deployments managed by ArgoCD for a private Amazon EKS cluster.

It acts as the single source of truth for all application workloads deployed via GitOps.

## Infrastructure
This repository works alongside the infrastructure layer:

👉 https://github.com/SuheyrM/Production-Grade-Private-EKS-Cluster-with-OpenVPN-Prometheus-Grafana

The infrastructure repo provisions:
- Amazon EKS cluster (private)
- VPC and networking
- OpenVPN access
- Monitoring stack (Prometheus + Grafana)
- ArgoCD installation
- 

## GitOps Workflow
```
GitHub → ArgoCD → Kubernetes Cluster
```
1. Code is pushed to this repository
2. ArgoCD detects changes
3. Applications are automatically synced to the EKS cluster

## Repository Structure

```
apps/
  demo-nginx/      # Sample stateless application
  rabbitmq/        # Stateful message broker (Helm)
  monitoring/      # Observability stack configs
```

## Applications

# demo-nginx
- Simple demo application
- Used to validate ArgoCD setup

# RabbitMQ
- Deployed via Bitnami Helm chart
- Stateful workload with persistent storage
- Exposes metrics for Prometheus

# Monitoring Stack 
- Integrated with kube-prometheus-stack
- Includes Prometheus, Grafana, Alertmanager
- Uses ServiceMonitor for scraping metrics

# Deployment Target
- Private EKS cluster (no public access)
- Access via OpenVPN
- Internal service communication only

# Applications are defined and managed using ArgoCD:

- ArgoCD continuously monitors this repository
- Automatically syncs changes to the EKS cluster
- Ensures desired state is always maintained (self-healing)

This enables a fully declarative GitOps workflow where Git is the single source of truth.

# System Architecture

```
Terraform → EKS Cluster → ArgoCD → GitHub (this repo) → Kubernetes Apps
```
# Purpose
This repository demonstrates a production-style GitOps workflow by separating infrastructure provisioning from application deployment, enabling automated, declarative Kubernetes operations.
