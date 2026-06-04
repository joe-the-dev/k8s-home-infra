# k8s-base — Home Infrastructure

This repo manages a home lab Kubernetes cluster declaratively (GitOps style).
The goal is to learn K8s while self-hosting real services.

## Cluster

- Distribution: k3s (lightweight, single-node or small cluster)
- GitOps tool: Flux or ArgoCD (TBD)
- Ingress: Traefik (k3s default) or Nginx
- Storage: local-path provisioner (k3s default)

## Repo Structure (target)

```
k8s-base/
├── apps/           # App-specific Helm values or raw manifests
│   └── <app-name>/
│       ├── namespace.yaml
│       ├── deployment.yaml
│       ├── service.yaml
│       └── ingress.yaml
├── base/           # Shared/cluster-wide resources
│   ├── namespaces/
│   └── storage/
├── helm/           # Helm chart overrides / HelmRelease resources
└── flux/           # Flux system manifests (if using Flux)
```

## Conventions

- One namespace per app
- Use Deployments (not bare Pods) for all workloads
- Always set resource requests and limits
- Store secrets as K8s Secrets (use Sealed Secrets or SOPS for GitOps-safe encryption — TBD)
- Use labels: `app.kubernetes.io/name`, `app.kubernetes.io/instance`

## Common Commands

```bash
# Cluster status
kubectl get nodes
kubectl get pods -A

# Apply a manifest
kubectl apply -f <file>

# Watch rollout
kubectl rollout status deployment/<name> -n <namespace>

# Logs
kubectl logs -f deployment/<name> -n <namespace>

# Describe a resource (debug)
kubectl describe pod/<name> -n <namespace>

# Delete a resource
kubectl delete -f <file>
```

## Learning Goals

- Understand core K8s objects: Pod, Deployment, Service, Ingress, ConfigMap, Secret
- Practice GitOps: cluster state lives in this repo, not ad-hoc commands
- Gradually add real home services (e.g. Home Assistant, Plex, Nginx, etc.)
