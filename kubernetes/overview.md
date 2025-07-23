# Kubernetes (K8s)

Kubernetes, também conhecido como **K8s**, foi criado pelo Google e é um projeto **open source** para orquestração de containers.

## Conceitos Fundamentais

Para entender o funcionamento do Kubernetes, é essencial conhecer dois conceitos principais:

- **Containers**
    
- **Orquestração de Containers**
    

## Containers

Um exemplo popular de tecnologia de containers é o **Docker**. Ele permite que sua aplicação seja empacotada junto com todas as suas dependências, garantindo que ela rode de forma consistente em diferentes ambientes.

### Benefícios do Docker:

- Facilita o desenvolvimento colaborativo ao manter um ambiente uniforme.
    
- Evita problemas de compatibilidade de versões entre os membros do time.
    
- Permite criar um ambiente isolado e reproduzível.
    
- Funciona como uma máquina virtual leve, mas apenas para rodar sua aplicação.
    

## Kubernetes

O Kubernetes é um **orquestrador de containers**, ou seja, ele gerencia múltiplos containers simultaneamente, garantindo alta disponibilidade e escalabilidade das aplicações.

### Conceitos Básicos do Kubernetes

#### **Nodes**

Um **node** é uma máquina física ou virtual onde os containers são executados.

#### **Cluster**

Um **cluster** é um conjunto de **nodes**, permitindo que, caso um node falhe, outro assuma suas funções para manter a aplicação funcionando.

#### **Master Node**

O **Master Node** é o responsável por gerenciar a orquestração dos containers. Ele monitora os **worker nodes**, garantindo que, se um deles falhar, a carga seja redistribuída.

## Componentes do Kubernetes

- **API Server** → Interface do Kubernetes para comunicação com o cluster.
    
- **etcd** → Banco de dados distribuído onde o estado do cluster é armazenado.
    
- **kubelet** → Agente que roda em cada node e garante que os containers estejam funcionando corretamente.
    
- **Container Runtime** → Tecnologia que roda os containers (exemplo: Docker, containerd).
    
- **Controller Manager** → Controla o estado desejado do cluster e mantém a integridade dos serviços.
    
- **Scheduler** → Responsável por alocar os containers nos nodes disponíveis.
    

## Tipos de Servidores no Kubernetes

- **Master Node** → Controla e gerencia o cluster.
    
- **Worker Node** → Executa os containers e aplicações.
    

## Comandos do `kubectl`

O `kubectl` é a ferramenta de linha de comando para gerenciar um cluster Kubernetes.

### Comandos úteis:

```bash
kubectl cluster-info # Exibe informações do cluster
kubectl get nodes    # Lista os nodes do cluster
```



