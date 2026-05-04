# kubernetes-deployment

Hands-on Kubernetes lab focused on core workload management: deploying containerized applications, exposing services, scaling replicas, and performing zero-downtime rolling updates.

---

## Stack

- Kubernetes (kubectl + kind / minikube)
- Docker
- YAML manifests

---

## Concepts Covered

- **Deployment** — declarative workload management
- **Service** — internal and external exposure (ClusterIP / NodePort)
- **Scaling** — manual replica scaling
- **Rolling Update** — zero-downtime image updates with rollback support

---

## Project Structure

```
kubernetes-deployment/
├── deployment.yaml
├── service.yaml
└── README.md
```

---

## Usage

**Apply manifests**
```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

**Check status**
```bash
kubectl get pods
kubectl get svc
```

**Scale replicas**
```bash
kubectl scale deployment <name> --replicas=<n>
```

**Rolling update**
```bash
kubectl set image deployment/<name> <container>=<image>:<tag>
```

**Rollback**
```bash
kubectl rollout undo deployment/<name>
```

---

## Context

Part of a progressive DevOps lab series covering Docker, CI/CD, monitoring, logging, and infrastructure as code.
