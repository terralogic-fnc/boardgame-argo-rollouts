# BoardGame – Canary Deployment with Argo Rollouts & AWS ALB

This repository contains Helm charts and Argo CD configuration
to deploy the **BoardGame Database application** using:

- Argo CD (GitOps)
- Argo Rollouts (Canary deployment)
- AWS ALB Ingress Controller
- Helm charts

---

## Architecture

User → AWS ALB → Ingress → Stable/Canary Services → Pods  
Traffic is progressively shifted using **Argo Rollouts**.

---

## Prerequisites

- Kubernetes cluster (EKS recommended)
- AWS ALB Ingress Controller installed
- Argo CD installed
- Argo Rollouts installed
- ACM certificate (optional for HTTPS)

---

## Repository Structure

