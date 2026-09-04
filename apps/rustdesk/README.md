# RustDesk

Manifests dos componentes RustDesk executados no cluster K3s.

## API

O Deployment `rustdesk-api` utiliza o Secret:

`rustdesk-api-secret`

O Secret contém as credenciais necessárias pela API e não é versionado no Git.

Chaves utilizadas pelo Deployment:

- `DATABASE_URL`
- `JWT_SECRET`
- `RUSTDESK_KEY`
- `ADMIN_PASSWORD`

Os valores devem existir diretamente no cluster Kubernetes.

## Aplicação

Para aplicar o Deployment:

`kubectl apply -f apps/rustdesk/deployment-api.yaml`

Para verificar o rollout:

`kubectl rollout status deployment/rustdesk-api`

Para verificar o Pod:

`kubectl get pods -l app=rustdesk-api`
