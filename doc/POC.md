# Getting access to ArgoCD

Here you can find steps to take to get access to ArgoCD. ArgoCD is Argo CD is a declarative continuous delivery tool for Kubernetes. 
It can be used as a standalone tool or as a part of your CI/CD workflow to deliver needed resources to your clusters.

## Install ArgoCD

TO install ArgoCD use the following code snippet:

`kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml`

This installs ArgoCD into your Kubernetes cluster.

## Access the ArgoCD UI

Once installed, you can access the ArgoCD UI using port-forwarding or by exposing the service externally:

`kubectl port-forward svc/argocd-server -n argocd 8080:443`

Open a browser and visit https://localhost:8080. You might need to accept the self-signed certificate to proceed.

## Login to ArgoCD

Use the default username and password to login:

`Username: admin
Password: <retrieve admin password>`

You can retrieve the admin password using:

`kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d && echo`

These steps will get you started with running ArgoCD.
