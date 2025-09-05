# Bem-vindo à Documentação do Sistema Lazarus

**Lazarus** é um sistema médico inteligente de última geração, construído com uma arquitetura de microsserviços robusta, escalável e resiliente. Esta documentação fornece um guia completo para entender, desenvolver, implantar e manter o sistema.

## O que é o Lazarus?

O Lazarus é uma plataforma completa para gestão hospitalar e assistência médica, com funcionalidades avançadas como:

- **Gestão de Pacientes**: Prontuários eletrônicos, histórico médico, agendamentos.
- **Procedimentos Cirúrgicos**: Planejamento, execução e acompanhamento.
- **Faturamento e Cobrança**: Gestão de contas, pagamentos e seguros.
- **Auditoria e Compliance**: Rastreamento completo de todas as ações.
- **Motor de Regras**: Workflows e decisões automatizadas com Camunda.
- **Chat com IA e RAG**: Assistente virtual inteligente com busca semântica.
- **API Gateway**: Ponto de entrada único, seguro e monitorado.

## Arquitetura

O sistema é composto por 9 microsserviços principais, cada um com sua própria responsabilidade e banco de dados. A comunicação entre eles é feita de forma assíncrona através do Kafka, garantindo desacoplamento e resiliência.

![Arquitetura Lazarus](assets/architecture.png)

## Como Usar esta Documentação

- **Arquitetura**: Entenda a visão geral do sistema, os microsserviços e os padrões de projeto utilizados.
- **Guias de Desenvolvimento**: Aprenda como configurar seu ambiente, seguir nossos padrões de código e contribuir com o projeto.
- **APIs**: Explore a documentação completa de todas as nossas APIs, com exemplos e detalhes de cada endpoint.
- **Deployment**: Siga nossos guias para implantar o sistema em diferentes ambientes.
- **Troubleshooting**: Encontre soluções para problemas comuns e aprenda a debugar o sistema.

## Primeiros Passos

Se você é um desenvolvedor, comece pelo [Guia de Ambiente de Desenvolvimento](./guides/dev-environment.md).

Se você é um administrador de sistemas, comece pelo [Guia de Deployment](./deployment/overview.md).

Se você quer entender a arquitetura, comece pela [Visão Geral da Arquitetura](./architecture/overview.md).

## Contribuição

O projeto Lazarus é de código aberto e aceitamos contribuições da comunidade. Para saber como contribuir, leia nosso [Guia de Contribuição](./guides/contributing.md).


