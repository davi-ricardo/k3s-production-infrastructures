# Estado atual da infraestrutura

## Cluster

O ambiente atual utiliza um cluster K3s de nó único.

Atualmente, os workloads de aplicação estão concentrados no namespace `default`.

## Aplicações

### RemoteOps / RustDesk

Os componentes da aplicação estão atualmente distribuídos entre:

- `rustdesk-api`
- `rustdesk-frontend`
- `rustdesk-hbbs`
- `rustdesk-hbbr`
- `rustdesk-postgres`

### GLPI

- `glpi-app`
- `glpi-db`

### Monitoramento

- `zabbix-server`
- `zabbix-web`
- `zabbix-postgres`
- `grafana`

## Services

Os serviços utilizam atualmente uma combinação de `ClusterIP` e `NodePort`.

Os componentes externos ainda utilizam NodePort, enquanto os componentes internos utilizam ClusterIP.

## Services redundantes identificados

Foram identificados dois Services adicionais:

- `api`
- `postgres`

O Service `api` possui o selector `app=rustdesk-api` e aponta para o mesmo endpoint do Service `rustdesk-api`.

O Service `postgres` possui o selector `app=zabbix-postgres` e aponta para o mesmo endpoint do Service `zabbix-postgres`.

Neste momento, eles **não devem ser removidos**.

A existência de referências a esses Services deverá ser investigada antes de qualquer alteração no ambiente de produção.

## Próximas etapas

1. Confirmar dependências dos Services redundantes.
2. Documentar os manifests atuais.
3. Criar manifests declarativos limpos.
4. Separar aplicações e infraestrutura no repositório.
5. Planejar namespaces.
6. Planejar armazenamento persistente.
7. Migrar configurações sensíveis para Secrets.
8. Planejar Ingress.
9. Validar alterações fora de produção quando possível.
10. Aplicar mudanças de forma incremental.
