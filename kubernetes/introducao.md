---
tags:
  - kubernetes
  - devops
  - orchestration
  - containers
related:
  - "[[overview]]"
  - "[[pods]]"
  - "[[Docker]]"
  - "[[Microsserviços]]"
creation-date: "2025-08-25"
---

# Introdução ao Kubernetes (K8s)

> [!NOTE] Summary
> **Kubernetes** (comumente abreviado como **K8s**) é uma plataforma de orquestração de contêineres open-source que automatiza a implantação, o dimensionamento e a gestão de aplicações em contêineres.

## Syntax

A sintaxe do Kubernetes é baseada em arquivos YAML que definem os objetos da API do Kubernetes.

### Exemplo de um Pod simples

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
```

## Use Cases

O Kubernetes é usado para resolver problemas como:

- **Reinicialização automática de contêineres:** Garante que um contêiner que falhou seja reiniciado.
- **Escalabilidade:** Aumenta ou diminui o número de contêineres com base na demanda.
- **Atualizações sem tempo de inatividade:** Permite atualizar uma aplicação para uma nova versão sem tempo de inatividade (rolling updates).
- **Descoberta de serviços:** Permite que os contêineres descubram e se comuniquem uns com os outros.

## See Also

- [[overview]]
- [[pods]]
- [[Docker]]
- [[Microsserviços]]

## References

- [Documentação Oficial do Kubernetes](https://kubernetes.io/docs/home/)
