# kubernetes-deployment

A hands-on Kubernetes lab focused on deploying, exposing, scaling, and managing containerized workloads in a local cluster.

The cluster runs with kind, while the workloads are defined through Kubernetes YAML manifests.

## What I practiced

The lab starts with an nginx Deployment running multiple replicas and covers the relationship between Deployments, ReplicaSets, and Pods.

I used both ClusterIP and NodePort Services to work with internal cluster communication and external access. I also practiced scaling the Deployment by changing the replica count and observing Kubernetes reconcile the desired state.

Rolling updates and rollbacks were tested by changing the nginx image version and following the rollout process until completion.

For workload reliability, the Deployment includes CPU and memory requests and limits, along with readiness and liveness probes.

The lab also covers namespaces as a way to separate workloads inside the same cluster.

## Stack

Kubernetes · kubectl · kind · Docker · YAML · nginx

## Usage

Create the cluster:

```bash
kind create cluster --config kind-config.yaml
