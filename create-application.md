1. Create a repostry and clone it into local
   
2. Create guestbook deployment file (source: https://github.com/argoproj/argocd-example-apps.git)
   ```bash
   apiVersion: apps/v1
   kind: Deployment
   metadata:
     name: guestbook-ui
   spec:
     replicas: 1
     revisionHistoryLimit: 3
     selector:
       matchLabels:
         app: guestbook-ui
     template:
       metadata:
         labels:
           app: guestbook-ui
       spec:
         containers:
           - image: gcr.io/google-samples/gb-frontend:v5
             name: guestbook-ui
             ports:
               - containerPort: 80
   ```
3. Create Service apiVersion: v1
   ```bash
   apiVersion: v1
   kind: Service
   metadata:
     name: guestbook-ui
   spec:
     ports:
     - port: 80
       targetPort: 80
     selector:
       app: guestbook-ui
   ```
4. Commit this into remote repository 