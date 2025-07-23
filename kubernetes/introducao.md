# Introdução ao Kubernetes (K8s)

**Kubernetes** (comumente abreviado como **K8s**) é uma plataforma de orquestração de contêineres open-source que automatiza a implantação, o dimensionamento e a gestão de aplicações em contêineres.

Originalmente desenvolvido pelo Google, agora é mantido pela Cloud Native Computing Foundation (CNCF). Ele funciona com uma variedade de runtimes de contêiner, incluindo o Docker.

Tags: #kubernetes #devops #orchestration #containers

---

## Problema que o Kubernetes Resolve

Imagine que você tem uma aplicação dividida em múltiplos microsserviços, cada um rodando em seu próprio contêiner. Gerenciar o ciclo de vida desses contêineres manualmente seria um pesadelo:

- Como você garante que um contêiner que falhou seja reiniciado?
- Como você aumenta ou diminui o número de contêineres com base na demanda (escalabilidade)?
- Como você atualiza uma aplicação para uma nova versão sem tempo de inatividade (rolling updates)?
- Como os contêineres descobrem e se comunicam uns com os outros?

O Kubernetes resolve esses e muitos outros problemas, fornecendo uma camada de abstração robusta para gerenciar clusters de máquinas (nós) como se fossem uma única entidade.

---

## Principais Conceitos

O Kubernetes tem um vocabulário próprio. Aqui estão os conceitos mais fundamentais:

- **[[Cluster]]**: Um conjunto de máquinas (físicas ou virtuais) chamadas de **[[Nós (Nodes)]]**, que executam aplicações em contêineres. Todo cluster tem pelo menos um Nó de Trabalho (Worker Node) e um Nó Mestre (Master Node).

- **[[Nó (Node)]]**: Uma máquina de trabalho no Kubernetes. Pode ser uma VM ou uma máquina física. O Nó Mestre gerencia os Nós de Trabalho.

- **[[Pod]]**: A menor e mais simples unidade de implantação no Kubernetes. Um Pod representa um grupo de um ou mais contêineres que são executados juntos e compartilham recursos (como rede e armazenamento). Geralmente, você tem um contêiner por Pod.

- **[[Deployment]]**: Um objeto que gerencia um conjunto de Pods replicados. Ele descreve o estado desejado e garante que o cluster corresponda a esse estado. Você usa Deployments para escalar sua aplicação e realizar atualizações.

- **[[Service]]**: Uma abstração que define uma forma de expor uma aplicação que está rodando em um conjunto de Pods. Services fornecem um ponto de acesso estável (um endereço IP e uma porta) para seus Pods, mesmo que os Pods sejam criados ou destruídos.

- **[[Namespace]]**: Uma forma de dividir os recursos do cluster em espaços virtuais. Útil para organizar, segregar e controlar o acesso a recursos em ambientes multi-tenant.

---

## Arquitetura Simplificada

```
+-----------------------+
|      Master Node      |
| (Control Plane)       |
|-----------------------|
| - API Server          |
| - etcd (banco de dados)|
| - Scheduler           |
| - Controller Manager  |
+-----------------------+
          |           
          | Gerencia
          |           
+-----------------------+      +-----------------------+
|      Worker Node 1    |      |      Worker Node 2    |
|-----------------------|      |-----------------------|
| - Kubelet             |      | - Kubelet             |
| - Kube-proxy          |      | - Kube-proxy          |
| - Container Runtime   |      | - Container Runtime   |
|   (ex: Docker)        |      |   (ex: Docker)        |
|-----------------------|      |-----------------------|
|   [Pod]   [Pod]       |      |   [Pod]   [Pod]       |
+-----------------------+      +-----------------------+
```

---

## Links Relacionados

- [[overview]]
- [[pods]]
- [[Docker]]
- [[Microsserviços]]