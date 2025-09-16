1. Get the eks cluster info 
   ```bash
   aws eks --region us-east-1 update-kubeconfig --name argocd
   ```
2. Set the cluster contenxt
   ```bash
   kubectl config current-context
   ```
3. Add cluster to ArgoCD
   ```bash
   argocd cluster add arn:aws:eks:us-east-1:553486498609:cluster/argocd
   ```