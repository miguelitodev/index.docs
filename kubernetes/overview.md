# Overview dos Componentes do Kubernetes

Um cluster Kubernetes funcional é composto por um conjunto de componentes que se dividem em duas categorias principais: o **Control Plane** (Plano de Controle) e os **Worker Nodes** (Nós de Trabalho).

Tags: #kubernetes #architecture #control-plane #nodes

---

## Control Plane (Master Node)

O Control Plane é o cérebro do cluster. Ele toma decisões globais sobre o cluster (como agendamento de [[pods]]) e detecta e responde a eventos do cluster. Os componentes do Control Plane podem ser executados em qualquer máquina no cluster, mas geralmente são executados juntos em uma ou mais máquinas dedicadas (Master Nodes).

### Componentes do Control Plane

- **`kube-apiserver` (API Server):**
  - Expõe a API do Kubernetes. É o *frontend* do Control Plane.
  - É por onde todas as ferramentas (como `kubectl`), componentes internos e usuários interagem com o cluster.

- **`etcd`:**
  - Um banco de dados chave-valor consistente e de alta disponibilidade.
  - Usado como o armazenamento de backup para todos os dados do cluster. É a "fonte da verdade" do Kubernetes.

- **`kube-scheduler` (Scheduler):**
  - Observa os Pods recém-criados que não têm um nó atribuído.
  - Seleciona um nó para o Pod ser executado com base em restrições de recursos, políticas e outras diretivas.

- **`kube-controller-manager` (Controller Manager):**
  - Executa os processos de controle (controllers).
  - Cada controller é um loop de controle que observa o estado do cluster através da API e faz as mudanças necessárias para levar o estado atual em direção ao estado desejado.
  - Exemplos: Node Controller, Replication Controller, Endpoints Controller.

- **`cloud-controller-manager` (Opcional):**
  - Executa controllers que interagem com provedores de nuvem (AWS, Azure, GCP).
  - Separa a lógica específica da nuvem da lógica principal do Kubernetes.

---

## Worker Nodes (Nós de Trabalho)

Os Worker Nodes são as máquinas (VMs ou físicas) que executam as cargas de trabalho (suas aplicações em contêineres).

### Componentes do Worker Node

- **`kubelet`:**
  - Um agente que roda em cada nó do cluster.
  - Garante que os contêineres descritos nos PodSpecs estejam rodando e saudáveis.
  - Ele não gerencia contêineres que não foram criados pelo Kubernetes.

- **`kube-proxy`:**
  - Um proxy de rede que roda em cada nó.
  - Mantém as regras de rede nos nós, permitindo a comunicação de rede para seus Pods a partir de sessões de rede dentro ou fora do seu cluster.
  - É o que torna o conceito de [[Service]] possível.

- **Container Runtime:**
  - O software responsável por executar os contêineres.
  - O Kubernetes suporta vários runtimes, como **Docker**, **containerd** e **CRI-O**.

---

## Links Relacionados

- [[introducao]]
- [[pods]]
- [[Service]]
- [[kubectl]] (a ferramenta de linha de comando para interagir com o API Server)