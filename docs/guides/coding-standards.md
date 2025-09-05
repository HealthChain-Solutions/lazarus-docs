# Padrões de Código

Este documento descreve os padrões de código e as melhores práticas a serem seguidas ao contribuir para o projeto Lazarus.

## Linguagem

- **TypeScript**: Todo o código de backend é escrito em TypeScript. Utilize a versão mais recente e os recursos modernos da linguagem.
- **Estilo**: Seguimos o guia de estilo do Airbnb para TypeScript, com algumas modificações. Utilize o ESLint e o Prettier para garantir a conformidade.

## Commits

- **Conventional Commits**: Todos os commits devem seguir a especificação [Conventional Commits](https://www.conventionalcommits.org/). Isso nos ajuda a gerar changelogs automaticamente e a manter um histórico de commits limpo e legível.

  Exemplos:

  - `feat(ms-patients): Adicionar endpoint para busca de pacientes por CPF`
  - `fix(ms-billing): Corrigir cálculo de juros em faturas atrasadas`
  - `docs(api-gateway): Atualizar documentação de rate limiting`

## Pull Requests

- **Templates**: Utilize o template de pull request fornecido no repositório.
- **Revisão**: Todos os pull requests devem ser revisados por pelo menos um outro membro da equipe antes de serem mesclados.
- **Testes**: Todos os pull requests devem incluir testes que cubram as novas funcionalidades ou correções.

## Arquitetura

- **Clean Architecture**: Seguimos os princípios da Clean Architecture para organizar nosso código em camadas (domain, application, infrastructure).
- **SOLID**: Siga os princípios SOLID para escrever código manutenível e escalável.
- **DRY (Don't Repeat Yourself)**: Evite duplicação de código. Utilize bibliotecas compartilhadas e funções utilitárias sempre que possível.

## Testes

- **Jest**: Utilizamos o Jest como nosso framework de testes.
- **Cobertura**: Buscamos uma cobertura de testes de pelo menos 80% para todo o código novo.
- **Tipos de Testes**: Escreva testes unitários, de integração e end-to-end para garantir a qualidade do software.

## Documentação

- **JSDoc**: Documente todas as funções, classes e tipos utilizando o JSDoc.
- **Swagger**: Utilize anotações do Swagger para documentar as APIs.
- **README**: Mantenha o README de cada microsserviço atualizado com informações relevantes.


