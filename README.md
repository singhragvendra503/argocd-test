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
