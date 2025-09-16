1. Create cluster.yaml file 

   ```bash
   apiVersion: eksctl.io/v1alpha5
   kind: ClusterConfig
   
   metadata:
     name: argocd
     region: us-east-1
     version: "1.32"
   
   vpc:
     id: "vpc-0fc0dc18b58b50dcd"
     subnets:
       public:
         us-east-1a:
           id: subnet-0087287ff9b250308
         us-east-1b:
           id: subnet-03628d1d8132c3a72
   
   nodeGroups:
     - name: public-ng-1
       instanceType: t3.medium
       desiredCapacity: 1
       minSize: 1
       maxSize: 1
       subnets:
         - us-east-1a
         - us-east-1b
       ssh:
         allow: true
   ```

2. Create eks cluster using below command
   ```bash
   eksctl create cluster -f cluster.yaml
   ```
3. Create namespace to install argocd
   ```bash
   kubectl create namespace argocd
   ```
4. Install argocd using below command
   ```bash
   kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
   ```
5. Expose argocd server using port forwarding
   ```bash 
   kubectl port-forward svc/argocd-server -n argocd 8080:443
   ```
6. Get initial password to login argocd
   ```bash
   kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d; echo
   ```
7. Access argocd UI using below URL
