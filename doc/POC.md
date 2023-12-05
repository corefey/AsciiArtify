# How to Run ArgoCD

ArgoCD is a popular tool used for continuous deployment and GitOps. To run ArgoCD, you need to follow these general steps:

### Prerequisites
1. **Kubernetes Cluster**: ArgoCD runs on Kubernetes. Ensure you have a cluster set up.
2. **kubectl**: Install `kubectl` to interact with your Kubernetes cluster.
3. **Helm**: It's often easier to install ArgoCD using Helm. Install Helm on your machine.
4. **Access to a Git Repository**: ArgoCD uses Git repositories to manage application configurations.

### Steps to Run ArgoCD
1. **Install ArgoCD using Helm**

   You can install ArgoCD via Helm by running:

    ```bash
    kubectl create namespace argocd
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
    ```

   This installs ArgoCD in your Kubernetes cluster.

2. **Access the ArgoCD UI**

   Once installed, you can access the ArgoCD UI using port-forwarding or by exposing the service externally:

    ```bash
    kubectl port-forward svc/argocd-server -n argocd 8080:443
    ```

   Open a browser and visit `https://localhost:8080`. You might need to accept the self-signed certificate to proceed.

3. **Login to ArgoCD**

   Use the default username and password to login:

    ```
    Username: admin
    Password: <retrieve admin password>
    ```

   You can retrieve the admin password using:

    ```bash
    kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d && echo
    ```

These steps will get you started with running ArgoCD.
