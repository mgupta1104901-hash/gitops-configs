# Project Infrastructure Overview

## Components

- **Infrastructure:** Azure Kubernetes Service (AKS) with **auto-scaling** enabled for dynamic workload management.  
- **GitOps Platform:** **Argo CD** for automated, continuous deployment and GitOps-based delivery.  
- **State Management:** **Terraform** for infrastructure provisioning, with optional **remote state** backend for team collaboration and consistency.  
- **Authentication:** **Azure Active Directory (AD)** integration for secure access control, along with local admin accounts for administrative operations.  
- **Networking:** **Azure CNI** networking model with **network policies** to manage traffic flow and enhance cluster security.  

---

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
