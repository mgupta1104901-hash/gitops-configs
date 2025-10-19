# Public IP Configuration in This Project

In this project, **four public IPs** are typically required:

1. **Nginx Ingress Controller**
2. **Argo CD**
3. **Application Load Balancer (LB)**
4. **Kubernetes Cluster Node IP**

However, since the **Azure Free Tier** subscription allows the creation of only **three public IPs**, adjustments were made to ensure the setup works within these limits.

## Adjustments Made

- The **Argo CD service** was changed from `ClusterIP` to **PublicIP** so it can be accessed locally using **kubectl port-forwarding** instead of requiring an additional external IP.
- The **DS-series VMs** (which are commonly used for AKS clusters) are **not available in the free tier**, so alternative VM types were selected to deploy the cluster successfully.

## Summary
These modifications allow the project to run completely under the **Azure Free Tier** constraints while still providing access to all essential components, including Argo CD and Nginx.
