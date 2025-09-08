# End-to-End-DevOps-Project

# 🚀 End-to-End DevOps Project on AWS with GitOps, CI/CD & Monitoring

This project demonstrates the implementation of a **real-world DevOps pipeline** on AWS using **Terraform, Kubernetes (EKS), Jenkins, GitHub Actions, ArgoCD, Prometheus & Grafana**.  

The goal is to provision a **fully automated and scalable environment** that supports continuous integration, continuous delivery, GitOps workflows, and advanced monitoring.

---

## 📋 Table of Contents
- [Project Overview](#-project-overview)
- [Architecture](#-architecture)
- [Tech Stack](#-tech-stack)
- [Prerequisites](#-prerequisites)
- [Quick Start](#-quick-start)
- [Detailed Setup Guide](#-detailed-setup-guide)
- [Monitoring & Alerts](#-monitoring--alerts)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🎯 Project Overview

This project implements a **complete GitOps workflow** with:
- **Infrastructure as Code (IaC)**: All AWS infrastructure provisioned using Terraform  
- **CI/CD Pipeline**: Jenkins automates build, test, and deployment  
- **GitOps Deployment**: ArgoCD continuously reconciles Kubernetes state with GitHub manifests  
- **Container Orchestration**: Kubernetes (EKS) handles scalable deployments  
- **Monitoring**: Prometheus scrapes cluster metrics, Grafana visualizes dashboards  
- **Security**: RBAC, secrets management, SSL certificates via ACM, and Route 53 for DNS  

The application used is a **Python Django app with MySQL**, containerized with Docker and deployed on AWS EKS with persistent storage (EFS).  

---

## 🏗️ Architecture

```text
┌───────────────┐     ┌─────────────┐     ┌───────────────┐
│   GitHub Repo │────▶│   Jenkins   │────▶│   ArgoCD      │
│ (App + GitOps)│     │ CI Pipeline │     │ GitOps Deploy │
└───────────────┘     └─────────────┘     └───────────────┘
                                                   │
                                                   ▼
                                        ┌─────────────────┐
                                        │   AWS EKS       │
                                        │  App + DB Pods  │
                                        └─────────────────┘
                                                   │
                                                   ▼
┌──────────────┐    ┌─────────────┐    ┌───────────────┐
│ Prometheus   │◀──▶│   Grafana   │    │   AlertManager │
└──────────────┘    └─────────────┘    └───────────────┘

┌──────────────┐    ┌─────────────┐    ┌───────────────┐
│ Route 53 DNS │───▶│ ACM (SSL)   │───▶│ AWS ALB       │
└──────────────┘    └─────────────┘    └───────────────┘

