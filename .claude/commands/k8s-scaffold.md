# Scaffold a Kubernetes App

Create a minimal but production-appropriate set of K8s manifests for a new home lab app.

Generate the following files under `apps/<app-name>/`:
- `namespace.yaml` — dedicated namespace
- `deployment.yaml` — Deployment with resource requests/limits, liveness + readiness probes
- `service.yaml` — ClusterIP Service
- `ingress.yaml` — Ingress (Traefik-compatible, with a placeholder hostname like `<app>.home.local`)
- `configmap.yaml` — if the app needs env config (omit if not needed)

Follow the conventions in CLAUDE.md:
- Labels: `app.kubernetes.io/name` and `app.kubernetes.io/instance`
- One namespace per app
- Resource limits set

After generating, briefly explain each file and what to customize.

App name and details: $ARGUMENTS
