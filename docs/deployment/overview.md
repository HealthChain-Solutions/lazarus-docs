# Visão Geral do Deployment

Este guia descreve como implantar o sistema Lazarus em diferentes ambientes.

## Ambientes

- **Desenvolvimento**: Ambiente local para desenvolvimento e testes.
- **Staging**: Ambiente de homologação, similar ao de produção.
- **Produção**: Ambiente final, utilizado pelos usuários.

## Tecnologias

- **Docker**: Para containerização dos microsserviços.
- **Kubernetes**: Para orquestração de contêineres em produção.
- **Helm**: Para gerenciamento de pacotes Kubernetes.
- **Azure**: Nossa plataforma de nuvem preferencial.

## Deployment em Desenvolvimento

O deployment em desenvolvimento é feito utilizando o Docker Compose. Para iniciar todos os serviços:

```bash
docker-compose up -d
```

Consulte o [Guia de Ambiente de Desenvolvimento](../guides/dev-environment.md) para mais detalhes.

## Deployment em Produção

O deployment em produção é feito utilizando Kubernetes e Helm. Os passos gerais são:

1. **Construir as imagens Docker** de cada microsserviço.
2. **Enviar as imagens** para um registro de contêineres (ex: Azure Container Registry).
3. **Configurar os charts Helm** com as variáveis de ambiente de produção.
4. **Implantar os charts** no cluster Kubernetes.

Consulte o [Guia de Deployment em Produção](./production.md) para um passo a passo detalhado.

## CI/CD

Utilizamos o GitHub Actions para nosso pipeline de CI/CD. O pipeline é responsável por:

- **Executar os testes** a cada push.
- **Construir as imagens Docker** em cada merge para a branch `main`.
- **Implantar em staging** automaticamente.
- **Implantar em produção** manualmente, após aprovação.

Consulte o [Guia de CI/CD](./ci-cd.md) para mais detalhes sobre o pipeline.


