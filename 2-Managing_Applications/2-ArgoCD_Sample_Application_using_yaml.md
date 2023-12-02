
## Defining Applications with YAML

Create a YAML file that defines your ArgoCD application. Here's an example YAML with explanations:

[0-Demo-Files/Nginx-Deployment-Argo-Apps/argo-app.yaml](../0-Demo-Files/Nginx-Deployment-Argo-Apps/argo-app.yaml)

- `CreateNamespace=true` allows ArgoCD to create the specified namespace if it does not already exist.
- `selfHeal` ensures that any manual changes made to the resources in the cluster are brought back to the state defined in Git.
- `prune` deletes resources in the cluster that are no longer present in the Git repository.

## Applying the YAML File

Once the YAML file is ready, apply it to your cluster with the following command:

```bash
kubectl apply -f argo-app.yaml -n argocd
```

This command creates the application as defined in the YAML file in ArgoCD, which then syncs the application state with the cluster. After running the command, ArgoCD will monitor the repository at the specified `repoURL` and path. Any changes pushed to the repository will be reflected in the Kubernetes cluster based on the sync policy defined.

## Delete the application

```bash
kubectl delete -f argo-app.yaml -n argocd
```