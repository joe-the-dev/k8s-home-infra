# Cluster Status Overview

Run a quick health check of the home lab cluster and summarize what's running.

Steps:
1. `kubectl get nodes` — node health
2. `kubectl get pods -A` — all pods across namespaces
3. `kubectl get deployments -A` — deployment readiness
4. `kubectl get ingress -A` — exposed services
5. Flag anything that looks unhealthy (CrashLoopBackOff, Pending, 0/1 ready, etc.)

Present a clean summary: what's healthy, what needs attention, and any next steps.
