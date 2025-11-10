## 🚀 Microservices DevOps Platform on AWS (Jenkins → ECR → ArgoCD → Istio → Prometheus → Grafana)

This project demonstrates a **complete end-to-end CI/CD pipeline** for a microservices-based Java web application, deployed and monitored on **AWS EKS (Elastic Kubernetes Service)**.  
It integrates industry-standard DevOps tools for automation, observability, and resilience — delivering a modern, production-ready setup.

---

## 🧠 Project Overview

### 🧩 Key Tools and Technologies
| Category | Tools Used |
|-----------|-------------|
| **Version Control** | GitHub |
| **CI/CD Automation** | Jenkins, GitHub Webhooks |
| **Containerization** | Docker, Amazon ECR |
| **Orchestration** | Kubernetes (EKS) |
| **Progressive Delivery** | ArgoCD, Argo Rollouts |
| **Service Mesh** | Istio |
| **Monitoring & Alerting** | Prometheus, Grafana, AWS SES |
| **Cloud Platform** | AWS (EKS, EC2, IAM, Load Balancer) |

---

## 🏗️ Architecture Overview

### 🔄 CI/CD Workflow
```

GitHub → Jenkins → Docker → ECR → ArgoCD → EKS → Istio → Prometheus → Grafana

Developer pushes code to GitHub.

Jenkins pipeline triggers automatically via webhook.

Jenkins:

Builds Docker image.

Pushes it to Amazon ECR.

Updates Helm values or Kubernetes manifests.

ArgoCD detects the manifest update and automatically deploys to EKS.

Istio handles routing, canary deployment, and traffic management.

Prometheus & Grafana monitor performance metrics and send alert emails through AWS SES.

```
🧩 Folder Structure

```text
microservices-devops-platform/
├── app/                        # Java microservice application code
├── jenkins/                    # Jenkinsfile and pipeline scripts
├── helm/                       # Helm charts for Kubernetes deployment
├── argo/                       # ArgoCD & Argo Rollout manifests
├── istio-1.28.0/               # Istio gateway and virtual service configs
├── alertmanager/               # Alertmanager configurations
├── grafana-dashboards/         # Grafana custom dashboards (JSON)
├── monitoring/                 # Prometheus & Grafana setup manifests
├── README.md                   # Project documentation
└── README_local.md             # Local environment setup
```

⚙️ Jenkins Pipeline Flow

Git Checkout

Maven Build

Docker Build & Push (to ECR)

Update Helm Chart Image Tag

Deploy to EKS via ArgoCD

Jenkinsfile contains dynamic image tag updates and automated Argo sync steps.

📸 Screenshot: Jenkins Pipeline


☸️ Kubernetes + ArgoCD Deployment

ArgoCD continuously monitors the GitHub repo for changes.

Istio routes live traffic between old and new versions (Canary).

Rollouts are automated and revert on health failure.

📸 Screenshot: ArgoCD Dashboard


📸 Screenshot: Istio Traffic Split


📈 Monitoring & Alerting (Prometheus + Grafana)

Prometheus collects application and system metrics.

Grafana visualizes key metrics like CPU, memory, and response latency.

AWS SES integrated with Grafana for email alerts.

🔔 Configured Alerts:

High CPU usage (> 0.2 core)

Node failures

Service downtime

📸 Screenshot: Grafana Alerts

📸 Screenshot: Alert Email

☁️ AWS Resources Used

EKS Cluster – multi-node Kubernetes cluster

EC2 Instances – Jenkins Master, Monitoring Node

Elastic Load Balancers – Public endpoints for Grafana, Prometheus, and App

IAM Roles & Policies – Jenkins, ArgoCD, and EKS integrations

S3 + ECR – artifact and image storage

📸 Screenshot: AWS Load Balancers


🧾 Key Highlights

✅ Fully automated CI/CD pipeline
✅ Argo Rollouts with progressive delivery
✅ Istio-based service mesh and traffic management
✅ Real-time monitoring and alerting with Grafana + AWS SES
✅ Infrastructure deployed on AWS EKS with autoscaling

🧩 Future Enhancements

Implement Terraform for complete infrastructure automation

Add centralized logging via ELK stack

Integrate Slack notifications for alerts

👨‍💻 Author

Abhin [DevOps Engineer]
🔗 GitHub: @abhin7821

📧 Email: abhin.devops01@gmail.com 

