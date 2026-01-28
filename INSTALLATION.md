### Install ArgoCD (GitOps Tool)

#### Check your Kubernetes cluster
```bash
kubectl get nodes
kubectl get pods -A
```

#### Install ArgoCD

```bash
kubectl create namespace argocd
```
```bash
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Check installation:
```bash
kubectl get pods -n argocd
```
After pod Running, go to next step

#### Expose ArgoCD Server (Access UI)
Option A (temporary port-forward)
```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443 --address 0.0.0.0
```

Open your Browser:
```url
https://localhost:8080
```
OR
```url
https://<SERVER-IP>:8080
```

#### ArgoCD Login Credentials
User: `admin`
Password:

```bash
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d
```

#### Create Your GitOps Repo (GitHub recommended)
Example repo structure:
```bash
gitops-repo/
 ├── apps/
 │    └── myapp/
 │         ├── deployment.yaml
 │         └── service.yaml
 └── kustomization.yaml
```






