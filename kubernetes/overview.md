---
tags:
  - kubernetes
  - architecture
  - control-plane
  - nodes
related:
  - "[[introducao]]"
  - "[[pods]]"
  - "[[Service]]"
  - "[[kubectl]]"
creation-date: "2025-08-25"
---

# Overview dos Componentes do Kubernetes

> [!NOTE] Summary
> Um cluster Kubernetes funcional é composto por um conjunto de componentes que se dividem em duas categorias principais: o **Control Plane** (Plano de Controle) e os **Worker Nodes** (Nós de Trabalho).

## Syntax

A sintaxe do Kubernetes é baseada em arquivos YAML que definem os objetos da API do Kubernetes.

### Exemplo de um Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

## Use Cases

- **Control Plane:** O cérebro do cluster, responsável por tomar decisões globais.
- **Worker Nodes:** As máquinas que executam as cargas de trabalho (suas aplicações em contêineres).

## See Also

- [[introducao]]
- [[pods]]
- [[Service]]
- [[kubectl]]

## References

- [Kubernetes Components](https://kubernetes.io/docs/concepts/overview/components/)
