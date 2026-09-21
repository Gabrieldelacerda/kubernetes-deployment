# kubernetes-deployment

A hands-on Kubernetes lab focused on deploying, exposing, scaling, and managing containerized workloads in a local cluster.

The cluster runs with kind, and the workloads are defined through Kubernetes YAML manifests.

## What I practiced

The lab starts with an nginx Deployment and covers the relationship between Deployments, ReplicaSets, and Pods.

I used ClusterIP and NodePort Services to work with internal and external access, then tested manual scaling by changing the number of replicas and observing how Kubernetes reconciles the desired state.

I also practiced rolling updates and rollbacks by changing the nginx image version and following the rollout process.

For workload reliability, I configured CPU and memory limits, along with readiness and liveness probes. Readiness probes control whether a Pod should receive traffic, while liveness probes allow Kubernetes to detect and restart unhealthy containers.

Finally, I used namespaces to deploy workloads into isolated environments within the same cluster.

## Stack

Kubernetes · kubectl · kind · Docker · YAML

## Commands

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

kubectl get pods
kubectl get svc

kubectl scale deployment <name> --replicas=<n>

kubectl set image deployment/<name> <container>=<image>:<tag>

kubectl rollout undo deployment/<name>

kubectl describe pod <pod-name>

kubectl apply -f deployment.yaml -n <namespace>
kubectl get pods -n <namespace>
```

## Context

Part of my DevOps and Cloud lab portfolio, covering infrastructure, automation, CI/CD, observability, and container orchestration.
