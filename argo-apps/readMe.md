# Argocd App of Apps patterns, using Kustomize

Basic way to set-up argocd.

## Create an argocd namespace in your cluster

```
kubectl create namespace argocd
```

## Install argocd in your cluster

```
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

## Download argocd onto your machine:

[download guide](https://argo-cd.readthedocs.io/en/stable/getting_started/#2-download-argo-cd-cli)

```
brew install argocd
```

## Forward a port from your local machine to the pod running the argocd-server

```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

## Get the admin password, to allow you to sign-in into the argo-ui

```
argocd admin initial-password -n argocd
```

OR

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"
```

And then decode the base64 string:

```
echo "<base64_string>" | base64 -D
```

## Open the argo ui

https://localhost:8080

## Login to argo on the cli:

```
argocd login localhost:8080
```

## Create the Argo App of Apps

```
argocd app create app-of-apps-practice \
--repo https://github.com/TluwaniMS/kustomize-practice-project.git \
--path argo-apps \
--revision master \
--dest-namespace argocd \
--dest-server https://kubernetes.default.svc \
--project default \
--sync-policy automated \
--auto-prune \
--self-heal \
--sync-option CreateNamespace=true
```