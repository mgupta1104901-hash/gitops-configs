# Project Infrastructure Overview

## Components

- **Infrastructure:** Azure Kubernetes Service (AKS) with **auto-scaling** enabled for dynamic workload management.  
- **GitOps Platform:** **Argo CD** for automated, continuous deployment and GitOps-based delivery.  
- **State Management:** **Terraform** for infrastructure provisioning, with optional **remote state** backend for team collaboration and consistency.  
- **Authentication:** **Azure Active Directory (AD)** integration for secure access control, along with local admin accounts for administrative operations.  
- **Networking:** **Azure CNI** networking model with **network policies** to manage traffic flow and enhance cluster security.  

---
# 🚀 AKS GitOps Deployment Guide

**Complete step-by-step guide to deploy AKS with GitOps using Terraform and Argo CD**

This repository provides a **production-ready setup** for deploying applications to **Azure Kubernetes Service (AKS)** using **GitOps principles**. By leveraging **Argo CD** and **Terraform**, this guide ensures automated, consistent, and scalable deployments to your Kubernetes cluster.  

## Key Features

- **Infrastructure as Code:** Provision AKS clusters using **Terraform**.  
- **GitOps Deployment:** Manage application deployments declaratively with **Argo CD**.  
- **Scalable & Secure:** AKS with **auto-scaling** and **Azure CNI network policies**.  
- **Authentication:** Integrates with **Azure AD** and supports local admin accounts.  
- **Version Controlled Deployments:** All manifests, Helm charts, and Kustomize configs are stored in Git for **auditability** and **reproducibility**.  


## Public IP Configuration

In this project, **four public IPs** are typically required:

1. **Nginx Ingress Controller**  
2. **Argo CD**  
3. **Application Load Balancer (LB)**  
4. **Kubernetes Cluster Node IP**

### Azure Free Tier Limitation

The **Azure Free Tier** allows a maximum of **three public IPs per subscription**.  
To work within these limits, the following changes were made:

- The **Argo CD service** was modified from `ClusterIP` to **PublicIP**, allowing access via **kubectl port-forwarding** instead of allocating an external IP.  
- Since **DS-series VMs** are **not available** under the free tier, alternative VM sizes were selected to ensure successful cluster deployment.  

---

## Summary

These configurations enable full functionality of the project within the **Azure Free Tier** constraints while maintaining:  
- Continuous deployment via **Argo CD**  
- Secure networking with **Azure CNI**  
- Scalable workloads on **AKS**  
- Automated provisioning using **Terraform**
