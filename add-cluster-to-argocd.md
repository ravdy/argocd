1. Set argocd cluster as current context 
   ```bash
   aws eks --region us-east-1 update-kubeconfig --name argocd
   ```
2. See the current context
   ```bash
   kubectl config current-context
   ```
3. Add cluster to ArgoCD
   ```bash
   argocd cluster add arn:aws:eks:us-east-1:553486498609:cluster/argocd
   ```