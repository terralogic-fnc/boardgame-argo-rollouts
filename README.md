# BoardGame – Canary Deployment with Argo Rollouts & AWS ALB

This repository contains a **production-grade GitOps setup** for deploying the **BoardGame Database application** on Kubernetes using:

- **Helm** for Kubernetes templating
- **Argo CD** for GitOps-based continuous delivery
- **Argo Rollouts** for Canary deployments
- **AWS ALB Ingress Controller** for traffic management

This setup enables **zero-downtime deployments**, **progressive traffic shifting**, and **instant rollbacks**.

---

## 🚀 Key Features

- Canary deployments using Argo Rollouts
- Native AWS ALB traffic splitting (no NGINX required)
- GitOps-driven deployments with Argo CD
- Environment-specific configuration (dev / prod)
- Zero-downtime application updates
- Safe and fast rollback mechanism

---
🧱 Architecture Overview
User
  │
  ▼

  
AWS Application Load Balancer (ALB)
  │
  ▼

  
Kubernetes Ingress
  │
  ▼

  
Argo Rollouts
  ├── Stable Service  (boardgame-svc)
  └── Canary Service  (boardgame-svc-preview)
          │
          ▼

          
      Application Pods



---

## 📁 Folder Structure

```text
boardgame-argo-rollouts/
├── README.md
│   # Project documentation
│
├── argocd/
│   └── boardgame-app.yaml
│       # Argo CD Application manifest (GitOps entry point)
│
├── helm/
│   └── boardgame/
│       ├── Chart.yaml
│       │   # Helm chart metadata
│       │
│       ├── values.yaml
│       │   # Default Helm values
│       │
│       ├── values-dev.yaml
│       │   # Development environment overrides
│       │
│       ├── values-prod.yaml
│       │   # Production environment overrides
│       │
│       └── templates/
│           ├── rollout.yaml
│           │   # Argo Rollouts Canary strategy
│           │
│           ├── service-stable.yaml
│           │   # Stable Kubernetes Service
│           │
│           ├── service-canary.yaml
│           │   # Canary (preview) Kubernetes Service
│           │
│           ├── ingress.yaml
│           │   # AWS ALB Ingress configuration
│           │
│           └── _helpers.tpl
│               # Helm helper templates (naming & labels)
