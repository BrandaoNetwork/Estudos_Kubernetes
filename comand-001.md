# Comandos Kubernetes - Abreviações Padrão

Esta tabela lista os principais comandos do **Kubernetes** com suas **abreviações padrão** fornecidas pelo `kubectl`. Estas abreviações são integradas e funcionam em qualquer cluster Kubernetes.

## Tabela de Comandos e Abreviações

| **Comando Completo**                     | **Abreviação Padrão** | **Descrição**                                      |
|------------------------------------------|-----------------------|--------------------------------------------------|
| `kubectl get namespaces`                 | `kubectl get ns`      | Lista todos os namespaces no cluster.            |
| `kubectl get pods`                       | `kubectl get po`      | Lista todos os pods no namespace atual.          |
| `kubectl get services`                   | `kubectl get svc`     | Lista todos os serviços no namespace atual.      |
| `kubectl get deployments`                | `kubectl get deploy`  | Lista todos os deployments no namespace atual.   |
| `kubectl get replicationcontrollers`     | `kubectl get rc`      | Lista todos os replication controllers.          |
| `kubectl get daemonsets`                 | `kubectl get ds`      | Lista todos os daemonsets.                       |
| `kubectl get statefulsets`               | `kubectl get sts`     | Lista todos os statefulsets.                     |
| `kubectl get jobs`                       | `kubectl get job`     | Lista todos os jobs no namespace atual.          |
| `kubectl get configmaps`                 | `kubectl get cm`      | Lista todos os ConfigMaps no namespace atual.    |
| `kubectl get persistentvolumeclaims`     | `kubectl get pvc`     | Lista todas as PersistentVolumeClaims.           |
| `kubectl get persistentvolumes`          | `kubectl get pv`      | Lista todos os PersistentVolumes.                |
| `kubectl describe namespaces`            | `kubectl describe ns` | Descreve detalhes de um namespace específico.    |
| `kubectl describe pods`                  | `kubectl describe po` | Descreve detalhes de um pod específico.          |
| `kubectl describe services`              | `kubectl describe svc`| Descreve detalhes de um serviço.                 |
| `kubectl create namespace <name>`        | `kubectl create ns`   | Cria um novo namespace.                          |
| `kubectl delete namespace <name>`        | `kubectl delete ns`   | Deleta um namespace específico.                  |
| `kubectl delete pods`                    | `kubectl delete po`   | Deleta um pod específico.                        |

## Exemplos de Uso

1. **Listar todos os namespaces:**
   ```bash
   kubectl get ns
   ```

2. **Listar pods no namespace atual:**
   ```bash
   kubectl get po
   ```

3. **Descrever um serviço específico:**
   ```bash
   kubectl describe svc <nome-do-serviço>
   ```

4. **Criar um namespace:**
   ```bash
   kubectl create ns <nome-do-namespace>
   ```

5. **Deletar um pod:**
   ```bash
   kubectl delete po <nome-do-pod>
   ```

## Conclusão

Estas abreviações padrão são práticas e ajudam a economizar tempo no gerenciamento do cluster Kubernetes. Elas estão disponíveis por padrão e funcionam sem necessidade de configuração adicional.
