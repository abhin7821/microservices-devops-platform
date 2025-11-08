# Microservices DevOps Platform (End-to-End CI/CD)

This repository contains a complete automated CI/CD pipeline:
**GitHub → Jenkins → ECR → ArgoCD → EKS → Istio → Prometheus → Grafana → Alertmanager.**

### Structure
- `app/` — source code and Dockerfile  
- `jenkins/` — Jenkins pipeline script  
- `helm/` — Helm chart for Kubernetes deployment  
- `argo/` — ArgoCD GitOps config

### Workflow
1. Jenkins builds Docker image and pushes to ECR  
2. Jenkins updates Helm chart image tag and pushes back to GitHub  
3. ArgoCD auto-syncs and deploys to EKS  
4. Prometheus + Grafana monitor, Alertmanager notifies issues via Slack
