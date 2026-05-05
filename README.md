(versão em português abaixo)

# kubernetes-deployment

A hands-on Kubernetes lab I built to get comfortable with the core concepts of running and managing containerized workloads in a cluster. The goal was never to memorize commands, but to actually understand what happens inside the cluster when you run them.

---

## Stack

Kubernetes (kubectl + kind), Docker, and YAML manifests. I used kind to run the cluster locally inside Docker containers — lightweight and straightforward for a lab environment.

---

## What I practiced

I started with a simple nginx Deployment and built up from there. The first thing I got comfortable with was the relationship between Deployments, ReplicaSets, and Pods — understanding that a Deployment doesn't run containers directly, it just declares intent and lets Kubernetes figure out the rest.

From there I exposed the app using two Service types: ClusterIP for internal cluster traffic, and NodePort for external access. I tested both to understand when you'd use one over the other.

I then practiced manual scaling — bumping replicas up and down and watching Kubernetes react in real time. After that, rolling updates: changing the nginx image version and observing how Kubernetes replaces Pods gradually without dropping traffic. I also triggered a rollback to confirm you can always go back to the previous version.

On the reliability side, I added resource limits to define CPU and memory boundaries per container, and configured liveness and readiness probes so Kubernetes knows when a Pod is healthy and when to pull it from rotation.

Finally, I used namespaces to deploy the same workload into isolated environments within the same cluster.

---

## Commands I used

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

**Inspect a Pod's probes and resource limits**
```bash
kubectl describe pod <pod-name>
```

**Deploy to a specific namespace**
```bash
kubectl apply -f deployment.yaml -n <namespace>
kubectl get pods -n <namespace>
```

---

## Context

Part of a progressive DevOps lab series I'm building, covering Docker, CI/CD, monitoring, logging, and infrastructure as code.


# kubernetes-deployment

Um laboratório prático de Kubernetes que criei para me familiarizar com os conceitos básicos de execução e gerenciamento de cargas de trabalho conteinerizadas em um cluster. O objetivo nunca foi memorizar comandos, mas sim entender o que acontece dentro do cluster quando os executamos.

---

## Stack

Kubernetes (kubectl + kind), Docker e manifestos YAML. Usei o kind para executar o cluster localmente dentro de contêineres Docker — leve e simples para um ambiente de laboratório.

---

## O que pratiquei

Comecei com um Deployment simples do nginx e fui aprimorando a partir daí. A primeira coisa com a qual me familiarizei foi a relação entre Deployments, ReplicaSets e Pods — entendendo que um Deployment não executa contêineres diretamente, ele apenas declara a intenção e deixa o Kubernetes cuidar do resto.

A partir daí, expus o aplicativo usando dois tipos de serviço: ClusterIP para tráfego interno do cluster e NodePort para acesso externo. Testei ambas as abordagens para entender quando usar uma em vez da outra.

Em seguida, pratiquei o escalonamento manual — aumentando e diminuindo o número de réplicas e observando a reação do Kubernetes em tempo real. Depois disso, pratiquei as atualizações contínuas: alterei a versão da imagem do nginx e observei como o Kubernetes substitui os Pods gradualmente, sem interromper o tráfego. Também acionei um rollback para confirmar que sempre é possível retornar à versão anterior.

Em relação à confiabilidade, adicionei limites de recursos para definir os limites de CPU e memória por contêiner e configurei sondas de atividade e prontidão para que o Kubernetes saiba quando um Pod está íntegro e quando removê-lo da rotação.

Por fim, usei namespaces para implantar a mesma carga de trabalho em ambientes isolados dentro do mesmo cluster.

---

## Comandos que utilizei

**Aplicar manifestos**
```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

**Verificar status**

```bash
kubectl get pods
kubectl get svc
```

**Escalar réplicas**

```bash
kubectl scale deployment <nome> --replicas=<n>
```

**Atualização contínua**

```bash
kubectl set image deployment/<nome> <container>=<imagem>:<tag>
```

**Reverter**

```bash
kubectl rollout undo deployment/<nome>
```

**Inspecionar as sondagens e os limites de recursos de um Pod**

```bash
kubectl describe pod <nome-do-pod>
```

**Implantar em um local específico namespace**
```bash
kubectl apply -f deployment.yaml -n <namespace>
kubectl get pods -n <namespace>
```

---

## Contexto

Parte de uma série progressiva de laboratórios de DevOps que estou desenvolvendo, abordando Docker, CI/CD, monitoramento, registro de logs e infraestrutura como código.
