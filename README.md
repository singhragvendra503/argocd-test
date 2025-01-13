## Create RBAC in argoCD. 
#### Update user name in the file `argocd-cm.yaml` with actual name.

- Apply above file:
```bash
kubectl apply -f argocd-cm.yaml
```
#### Update user role in the file `argocd-rbac-cm.yaml` what access do you want to user.
- Apply above file:
```bash
kubectl apply -f argocd-cm.yaml
```
- Update user's password
```bash
argocd account update-password - account <username> - new-password <passowrd>
# Example
argocd account update-password - account peter - new-password test@1#
```

## Configure multiple cluster such as EKS, GKE, AKS, and an on-premises cluster

### 1. Install ArgoCD on a Single Cluster (Central Cluster)

### 2. Connect Remote Clusters to the Central ArgoCD Instance
- To add each cluster (EKS, GKE, AKS, on-prem) to the central ArgoCD instance, you need to use the argocd cluster add command. This will allow ArgoCD to manage these clusters.

#### Connect an EKS Cluster:
- Set up the kubectl context for your EKS cluster:
```bash
aws eks --region <region> update-kubeconfig --name <cluster-name>
```
- Add the EKS cluster to ArgoCD:
```bash
argocd cluster add <eks-context>
```
#### Connect a GKE Cluster:
- Set up the kubectl context for your GKE cluster:
```bash
gcloud container clusters get-credentials <cluster-name> --region <region> --project <project-id>
```
- Add the GKE cluster to ArgoCD:
```bash
argocd cluster add <gke-context>
```
#### Connect an AKS Cluster:
- Set up the kubectl context for your AKS cluster:
```bash
az aks get-credentials --resource-group <resource-group> --name <aks-cluster-name>
```
- Add the AKS cluster to ArgoCD:
```bash
argocd cluster add <aks-context>
```
#### Connect an On-Prem Cluster:
- Set up the kubectl context for your on-prem Kubernetes cluster (via kubeconfig or direct connection).
- Add the on-prem cluster to ArgoCD:
```bash
argocd cluster add <on-prem-context>
```

### 3. Verify Cluster Connections in ArgoCD

```bash
argocd cluster list
```
