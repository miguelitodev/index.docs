---
tags:
  - kubernetes
  - pods
  - workloads
  - containers
related:
  - "[[Deployment]]"
  - "[[StatefulSet]]"
  - "[[Service]]"
  - "[[Container Runtime]]"
  - "[[Padrão Sidecar]]"
creation-date: "2025-08-25"
---

# Pods no Kubernetes

> [!NOTE] Summary
> Um **Pod** é a menor e mais simples unidade de implantação que pode ser criada e gerenciada no Kubernetes. Ele representa uma única instância de uma aplicação em execução no seu cluster.

## Syntax

### Exemplo de Definição de Pod (YAML)

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod-example
  labels:
    app: webserver
spec:
  containers:
  - name: nginx-container
    image: nginx:1.21.6 # Imagem do Docker Hub
    ports:
    - containerPort: 80 # Porta que o contêiner expõe
```

**Como aplicar:**

```bash
kubectl apply -f nome-do-arquivo.yaml
```

## Use Cases

- **Single-container pods:** O caso de uso mais comum, onde um Pod executa um único contêiner.
- **Multi-container pods (Sidecar):** Para casos de uso específicos onde os contêineres estão fortemente acoplados, como logging, service mesh proxies, etc.

## See Also

- [[Deployment]]
- [[StatefulSet]]
- [[Service]]
- [[Container Runtime]]
- [[Padrão Sidecar]]

## References

- [Kubernetes Docs: Pods](https://kubernetes.io/docs/concepts/workloads/pods/)