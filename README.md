## EKS-GitOpa

This repository contains Kubernetes manifests managed by ArgoCD to deploy applications into a private EKS cluster.

It serves as the source of truth for all workloads deployed via GitOps.

## GitOps Workflow
```
GitHub → ArgoCD → Kubernetes Cluster
```
- Changes pushed to this repo
- ArgoCD detects changes
- Automatically syncs to cluster

## Repository Structure

```
apps/
  demo-nginx/
  rabbitmq/
  monitoring/
```

## Applications

# demo-nginx
- Simple demo application
- Used to validate ArgoCD setup

# RabbitMQ
- Stateful message broker
- Deployed via Helm chart
- Used for messaging and observability demo

# Monitoring Stack 
- Prometheus
- Grafana
- Alertmanager
- kube-prometheus-stack

# Deployment Target
- Private EKS cluster
- Access via OpenVPN
- No public exposure

# ArgoCD Integration
- Applications defined in ArgoCD
- Synced from this repository
- Enables declarative infrastructure

# Purpose
This repository demonstrates GitOps-based application deployment in a production-style Kubernetes environment.
