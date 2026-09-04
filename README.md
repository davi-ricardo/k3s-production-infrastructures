# RemoteOps Infrastructure

Infraestrutura Kubernetes responsável pela execução, administração e documentação dos serviços do ambiente RemoteOps.

Este repositório funciona como a **fonte de referência da infraestrutura do cluster K3s**, reunindo manifests, configurações, documentação e procedimentos necessários para administrar o ambiente de forma organizada e reproduzível.

---

## 🎯 Objetivo

O objetivo deste projeto é transformar a infraestrutura atualmente executada em K3s em uma estrutura:

- versionada com Git;
- documentada;
- organizada por responsabilidade;
- reproduzível;
- segura;
- preparada para automação e CI/CD;
- adequada para evolução futura para GitOps.

O repositório não representa apenas o RemoteOps. Ele contempla os serviços e componentes que compõem o ambiente Kubernetes como um todo.

---

## 🏗️ Ambiente

O ambiente atualmente utiliza:

- **K3s** — Kubernetes
- **Traefik** — Ingress / Reverse Proxy
- **PostgreSQL** — Bancos de dados
- **MariaDB** — Banco utilizado pelo GLPI
- **Grafana** — Visualização e dashboards
- **Zabbix** — Monitoramento
- **GLPI** — Gestão de ativos e serviços de TI
- **RustDesk** — Acesso remoto
- **RemoteOps** — Plataforma de gerenciamento

O cluster atualmente é executado em um único nó.

---

## 📁 Estrutura

```text
RemoteOps-Infrastructure/
├── apps/
│   ├── remoteops/
│   ├── rustdesk/
│   ├── glpi/
│   ├── zabbix/
│   └── grafana/
│
├── infrastructure/
│   ├── namespaces/
│   ├── networking/
│   ├── storage/
│   └── ingress/
│
├── monitoring/
│   ├── grafana/
│   └── zabbix/
│
├── scripts/
│
├── docs/
│   └── inventory/
│
├── .gitignore
└── README.md
