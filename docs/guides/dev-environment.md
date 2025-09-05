# Guia de Ambiente de Desenvolvimento

Este guia descreve como configurar seu ambiente de desenvolvimento para trabalhar no sistema Lazarus.

## Pré-requisitos

- **Node.js**: Versão 18.x ou superior
- **Docker**: Versão 20.x ou superior
- **Docker Compose**: Versão 2.x ou superior
- **Git**: Versão 2.x ou superior
- **pnpm**: Versão 8.x ou superior

## Configuração Inicial

1. **Clone o repositório**:

   ```bash
   git clone https://github.com/lazarus-project/lazarus.git
   cd lazarus
   ```

2. **Instale as dependências**:

   ```bash
   pnpm install
   ```

3. **Configure as variáveis de ambiente**:

   Copie o arquivo `.env.example` para `.env` e preencha as variáveis necessárias para cada microsserviço.

   ```bash
   cp .env.example .env
   ```

## Executando os Microsserviços

Você pode executar todos os microsserviços de uma vez utilizando o Docker Compose:

```bash
docker-compose up -d
```

Para executar um microsserviço individualmente:

```bash
pnpm --filter ms-patients dev
```

## Bancos de Dados

Os bancos de dados (PostgreSQL, MongoDB, Redis) são gerenciados pelo Docker Compose. Para acessá-los:

- **PostgreSQL**: `psql -h localhost -p 5432 -U user -d lazarus`
- **MongoDB**: `mongosh mongodb://localhost:27017/lazarus`
- **Redis**: `redis-cli -h localhost -p 6379`

## Kafka

O Kafka também é gerenciado pelo Docker Compose. Para interagir com os tópicos, você pode usar as ferramentas de linha de comando do Kafka ou a interface web do Kafka UI, disponível em `http://localhost:8080`.

## Testes

Para executar os testes de um microsserviço:

```bash
pnpm --filter ms-patients test
```

Para executar todos os testes:

```bash
pnpm test
```

## Debugging

Todos os microsserviços são configurados para permitir debugging remoto na porta `9229`. Você pode anexar seu debugger a essa porta para inspecionar o código em tempo de execução.


