# 🚀 DevOps Webpage CI/CD Pipeline

A complete end-to-end DevOps project demonstrating how a simple web application can be automatically built, tested, containerized, deployed, updated, scaled, rolled back, and exposed securely over HTTPS using Jenkins, Docker, and Kubernetes.

The project is built locally on Windows using Docker Desktop and Minikube, making it possible to practice a production-style DevOps workflow without requiring paid cloud infrastructure.

---

## 📌 Project Overview

This project demonstrates a complete CI/CD workflow:

```text
Developer
   │
   │ git push
   ▼
GitHub
   │
   │ Webhook / SCM polling
   ▼
Jenkins
   │
   ├── Checkout source code
   ├── Build Docker image
   ├── Run container test
   ├── Load image into Minikube
   ├── Validate Kubernetes cluster
   └── Deploy application
          │
          ▼
      Kubernetes
          │
          ├── Deployment
          │      ├── 2 replicas
          │      ├── Rolling Updates
          │      ├── Readiness Probe
          │      ├── Liveness Probe
          │      └── CPU Resources
          │
          ├── Service
          │
          ├── HPA
          │
          └── NGINX Ingress
                 │
                 ├── Host-based routing
                 └── TLS / HTTPS
                        │
                        ▼
                 https://myweb.local
