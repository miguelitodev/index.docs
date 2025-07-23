# Pods no Kubernetes

Um **Pod** é a menor e mais simples unidade de implantação que pode ser criada e gerenciada no Kubernetes. Ele representa uma única instância de uma aplicação em execução no seu cluster.

Um Pod pode conter um ou mais contêineres, mas o caso de uso mais comum é um **único contêiner por Pod**.

Tags: #kubernetes #pods #workloads #containers

---

## O que um Pod representa?

Um Pod encapsula:

- **Um ou mais contêineres:** (ex: Docker, containerd).
- **Recursos de armazenamento compartilhados:** Volumes que podem ser montados pelos contêineres.
- **Opções de rede:** Um endereço IP único no cluster, que é compartilhado por todos os contêineres dentro do Pod.
- **Informações sobre como executar cada contêiner:** Como a versão da imagem do contêiner, portas a serem usadas, etc.

Todos os contêineres em um Pod compartilham o mesmo ciclo de vida e os mesmos recursos de rede (IP e portas). Eles podem se comunicar uns com os outros usando `localhost`.

---

## Por que múltiplos contêineres?

Embora um contêiner por Pod seja o padrão, você pode ter múltiplos contêineres em um Pod para casos de uso específicos, geralmente quando eles estão fortemente acoplados. Este padrão é chamado de **Sidecar**.

Exemplos de Sidecars:

- **Logging:** Um contêiner que coleta logs do contêiner principal e os envia para um sistema centralizado.
- **Service Mesh Proxy:** Um proxy (como Envoy ou Linkerd) que gerencia o tráfego de rede para o contêiner principal.
- **Data Puller:** Um contêiner que busca dados ou atualizações de uma fonte externa e os disponibiliza para o contêiner principal (ex: `git sync`).

---

## Ciclo de Vida do Pod

Pods são considerados **efêmeros** e **descartáveis**. Eles não se curam sozinhos. Se um Pod falha ou é encerrado, ele não é reiniciado. Em vez disso, controladores de nível superior, como [[Deployment]] ou [[StatefulSet]], são responsáveis por criar um novo Pod para substituí-lo.

Por causa disso, você raramente cria Pods diretamente. Você quase sempre os cria e gerencia usando um controlador.

### Fases do Pod

- **Pending:** O Pod foi aceito pelo cluster, mas um ou mais de seus contêineres ainda não foram criados. Isso inclui o tempo para baixar a imagem.
- **Running:** O Pod foi vinculado a um [[Nó (Node)]] e todos os seus contêineres foram criados. Pelo menos um contêiner ainda está em execução, ou está no processo de iniciar ou reiniciar.
- **Succeeded:** Todos os contêineres no Pod foram encerrados com sucesso (código de saída 0) e não serão reiniciados. (Típico para Jobs).
- **Failed:** Todos os contêineres no Pod foram encerrados, e pelo menos um contêiner foi encerrado com falha (código de saída diferente de 0).
- **Unknown:** O estado do Pod não pôde ser obtido, geralmente devido a um erro de comunicação com o nó onde o Pod deveria estar.

---

## Exemplo de Definição de Pod (YAML)

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

---

## Links Relacionados

- [[Deployment]]
- [[StatefulSet]]
- [[Service]]
- [[Container Runtime]]
- [[Padrão Sidecar]]
