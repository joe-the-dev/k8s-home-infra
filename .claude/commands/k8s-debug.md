# Debug a Kubernetes Issue

Help diagnose a K8s problem. Run the relevant kubectl commands to investigate, then explain:
1. What the error or symptom means
2. The most likely root cause
3. How to fix it
4. How to prevent it in future manifests

Common things to check:
- Pod status and events: `kubectl describe pod/<name> -n <ns>`
- Logs: `kubectl logs <pod> -n <ns>`
- Deployment rollout: `kubectl rollout status deployment/<name> -n <ns>`
- Service endpoints: `kubectl get endpoints -n <ns>`
- Ingress: `kubectl describe ingress -n <ns>`

Always explain WHY something went wrong, not just how to fix it — the goal is learning.

Issue or resource to debug: $ARGUMENTS
