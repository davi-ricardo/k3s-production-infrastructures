# k3s-cluster-infrastructure

Este repositório representa a infraestrutura e a orquestração do cluster K3s como recurso versionado, organizado e documentado.

O escopo deste projeto é manter a camada de infraestrutura do ambiente em GitHub, incluindo a organização dos manifests Kubernetes, a documentação do estado atual do cluster, o inventário de workloads, serviços, namespaces, storage, networking e a base para evolução futura de automação, CI/CD e GitOps.

Este repositório não é o projeto de desenvolvimento do RemoteOps. RemoteOps, RustDesk, GLPI, Zabbix e Grafana são workloads executados no cluster. O código-fonte e o desenvolvimento individual dessas aplicações não pertencem a este repositório.

---

## Propósito do projeto

O propósito deste projeto é centralizar, versionar e documentar a infraestrutura do cluster K3s de produção.

A proposta principal é:

- organizar a infraestrutura do cluster em diretórios e manifests;
- manter um histórico de mudanças no Git;
- registrar o estado atual conhecido do ambiente;
- documentar workloads, serviços, namespaces, storage, networking e inventário;
- facilitar manutenção, troubleshooting e aprendizado;
- preparar a base para automação futura, CI/CD e GitOps.

Em outras palavras, este repositório é a fonte de verdade organizacional para a infraestrutura do cluster, e não a base de desenvolvimento das aplicações.

---

## Visão de arquitetura

A relação conceitual entre os elementos do ambiente é:

```text
Workstation CachyOS
    ↓
VS Code
    ↓
Git
    ↓
GitHub
    ↓
Cluster K3s
    ↓
Aplicações e serviços
```

O fluxo indica a forma como a infraestrutura é criada, documentada e versionada: a estação de trabalho administra arquivos e manifests em Git, que são armazenados em GitHub e aplicados ao cluster K3s. Os workloads e serviços do cluster são executados dentro do ambiente Kubernetes.

---

## Workloads atualmente administrados pelo projeto

Este repositório organiza os workloads e componentes que estão sendo executados ou considerados no cluster K3s. O foco documental é a infraestrutura desses workloads e não o desenvolvimento individual deles.

Os principais workloads observados na estrutura atual são:

- RemoteOps: aplicação/workload que deve ser tratada como uma aplicação executada no cluster. Seu desenvolvimento e código-fonte pertencem a um projeto separado.
- RustDesk: workload de acesso remoto e serviços relacionados.
- GLPI: workload de gestão de ativos e serviços de TI.
- Zabbix: workload de monitoramento e coleta.
- Grafana: workload de visualização e dashboards.

Essas aplicações são workloads do cluster K3s e devem ser tratadas como parte do ecossistema executado pela infraestrutura, sem que o desenvolvimento individual delas seja versionado neste repositório.

---

## Estrutura de diretórios

A organização atual do repositório é a seguinte:

```text
k3s-cluster-infrastructure/
├── apps/
│   ├── remoteops/
│   ├── rustdesk/
│   └── glpi/
├── monitoring/
│   ├── zabbix/
│   └── grafana/
├── infrastructure/
│   ├── namespaces/
│   ├── networking/
│   └── storage/
├── scripts/
└── docs/
    ├── architecture/
    │   └── current-state.md
    └── inventory/
        ├── configmaps.txt
        ├── deployments.txt
        ├── ingress.txt
        ├── namespaces.txt
        ├── nodes.txt
        ├── pods.txt
        ├── services.txt
        ├── storage.txt
        └── workloads.txt
```

Diretórios e papel esperado:

- apps/: organização dos manifests e recursos de workloads de aplicações, como RemoteOps, RustDesk e GLPI.
- monitoring/: organização de recursos de observabilidade e monitoramento, como Zabbix e Grafana.
- infrastructure/: recursos de infraestrutura do cluster, como namespaces, networking, storage e, no futuro, organização complementar para ingress.
- scripts/: scripts auxiliares de apoio administrativo, inspeção e automação.
- docs/: documentação e inventário do ambiente atual, incluindo arquitetura e registros do cluster.

---

## Inventário do estado atual

A pasta docs/inventory contém informações do estado atual do cluster, incluindo:

- nodes
- pods
- deployments
- services
- namespaces
- storage
- ingress
- configmaps
- workloads

Esse inventário é uma documentação viva do ambiente e deve ser tratada como material de referência para inspeção, manutenção e evolução da infraestrutura.

---

## Arquitetura atual

A referência de arquitetura atual está em:

docs/architecture/current-state.md

Esse documento representa o estado atual conhecido da infraestrutura do cluster, com informações sobre workloads, services, namespaces e etapas futuras de organização.

---

## Segurança

Este repositório deve manter uma abordagem cuidadosa com informações sensíveis.

Regras básicas:

- credenciais e secrets não devem ser commitados no Git;
- kubeconfigs não devem ser versionados;
- arquivos .env e qualquer arquivo com credenciais devem permanecer fora do repositório;
- manifests Kubernetes podem referenciar Secrets já existentes sem expor seus valores;
- valores sensíveis devem ser tratados futuramente com uma estratégia adequada de gerenciamento de secrets.

Nenhuma credencial real deve aparecer no repositório ou na documentação.

---

## Fluxo de trabalho recomendado

A manutenção deste repositório deve ocorrer de forma controlada e rastreável. O fluxo recomendado é:

1. Inspecionar o estado atual do cluster.
2. Documentar ou inventariar quando necessário.
3. Criar ou atualizar o manifesto.
4. Validar o YAML.
5. Executar dry-run ou diff quando apropriado.
6. Aplicar no cluster somente quando a alteração estiver validada.
7. Verificar rollout e status.
8. Fazer commit.
9. Fazer push para o GitHub.

Mudanças em produção devem ser tratadas com preparação, validação e acompanhamento.

---

## Tecnologias

As tecnologias principais observadas e utilizadas nesse contexto de infraestrutura são:

- Kubernetes
- K3s
- kubectl
- Git
- GitHub
- VS Code
- CachyOS/Linux

Também aparecem workloads e tecnologias relacionadas ao ecossistema de aplicações executadas no cluster:

- RustDesk
- GLPI
- Zabbix
- Grafana

Essas tecnologias devem ser entendidas como parte do ambiente operacional e do conjunto de workloads executados dentro do cluster K3s.

---

## Estado atual e evolução

Este projeto está em evolução e mantém uma visão de organização progressiva da infraestrutura do cluster.

As etapas conceituais observadas são:

- Fundação e organização do projeto
- Inventário do cluster
- Versionamento dos workloads
- Organização de secrets
- Organização de storage
- Networking e ingress
- Automação
- CI/CD
- GitOps

A evolução do projeto deve respeitar o que já foi comprovado no repositório e o que pode ser organizado em etapas futuras.

---

## Aprendizado

Este repositório também funciona como laboratório de aprendizado prático em infraestrutura Kubernetes. Sua finalidade didática inclui:

- estudar Kubernetes e K3s;
- praticar kubectl;
- aprender a escrever e organizar manifests;
- compreender deployments, services, secrets, storage e networking;
- aprender administração de infraestrutura como código;
- preparar a base para estudos futuros de CI/CD, automação e GitOps.

---

## Comandos básicos

Os seguintes comandos são úteis para inspeção de infraestrutura e devem ser usados com cuidado:

```bash
kubectl get nodes
kubectl get pods -A
kubectl get deployments -A
kubectl get services -A
kubectl get namespaces
kubectl config get-contexts
```

Esses comandos ajudam a validar o estado do cluster e os recursos disponíveis.

---

## Contribuição e manutenção

As mudanças neste repositório devem ser pequenas, rastreáveis e documentadas. A manutenção deve seguir uma convenção de clareza entre:

- inspeção do ambiente;
- atualização do inventário;
- criação ou edição de manifests;
- validação de sintaxe;
- verificação e aplicação controlada;
- commit com descrição adequada.

A documentação precisa acompanhar as alterações de infraestrutura para manter o repositório coerente.

---

## Licença

A licença deste repositório ainda não foi definida. Esta seção não será criada ou inventada.
