# Diagramas de Arquitetura

Esta seção contém diagramas detalhados que ilustram a arquitetura do sistema Lazarus.

## Diagrama de Contexto

O diagrama de contexto mostra o sistema Lazarus como uma caixa preta, interagindo com seus usuários e outros sistemas.

```mermaid
C4Context
  title Diagrama de Contexto do Sistema Lazarus

  Person(medico, "Médico")
  Person(paciente, "Paciente")
  Person(admin, "Administrador")

  System(lazarus, "Sistema Lazarus", "Sistema médico inteligente")

  System_Ext(hospital, "Sistema Hospitalar Externo")
  System_Ext(seguradora, "Sistema de Seguradora")

  Rel(medico, lazarus, "Utiliza")
  Rel(paciente, lazarus, "Utiliza")
  Rel(admin, lazarus, "Administra")

  Rel(lazarus, hospital, "Integra com")
  Rel(lazarus, seguradora, "Integra com")
```

## Diagrama de Contêineres

O diagrama de contêineres mostra os principais componentes de alto nível do sistema Lazarus e como eles interagem.

```mermaid
C4Container
  title Diagrama de Contêineres do Sistema Lazarus

  Person(medico, "Médico")
  Person(paciente, "Paciente")

  System_Boundary(lazarus, "Sistema Lazarus") {
    Container(spa, "Single-Page App", "JavaScript, React", "Interface do usuário")
    Container(api_gateway, "API Gateway", "Kong, Nginx", "Ponto de entrada da API")
    Container(ms_patients, "Microsserviço de Pacientes", "Node.js, TypeScript", "Gerencia dados de pacientes")
    Container(ms_procedures, "Microsserviço de Procedimentos", "Node.js, TypeScript", "Gerencia dados de procedimentos")
    Container(ms_billing, "Microsserviço de Faturamento", "Node.js, TypeScript", "Gerencia dados de faturamento")
    Container(rag_api, "API RAG", "Python, Flask", "Chat com IA e busca semântica")
    Container(kafka, "Kafka", "Apache Kafka", "Plataforma de streaming de eventos")
    ContainerDb(db_postgres, "Banco de Dados (PostgreSQL)", "PostgreSQL", "Armazena dados relacionais")
    ContainerDb(db_mongo, "Banco de Dados (MongoDB)", "MongoDB", "Armazena dados de leitura (CQRS)")
    ContainerDb(db_weaviate, "Banco Vetorial (Weaviate)", "Weaviate", "Armazena embeddings para busca semântica")
  }

  Rel(medico, spa, "Utiliza", "HTTPS")
  Rel(paciente, spa, "Utiliza", "HTTPS")

  Rel(spa, api_gateway, "Chama API", "HTTPS")

  Rel(api_gateway, ms_patients, "Roteia para", "HTTP")
  Rel(api_gateway, ms_procedures, "Roteia para", "HTTP")
  Rel(api_gateway, ms_billing, "Roteia para", "HTTP")
  Rel(api_gateway, rag_api, "Roteia para", "HTTP")

  Rel(ms_patients, db_postgres, "Escreve em", "TCP")
  Rel(ms_procedures, db_postgres, "Escreve em", "TCP")
  Rel(ms_billing, db_postgres, "Escreve em", "TCP")

  Rel(ms_patients, kafka, "Publica eventos em")
  Rel(ms_procedures, kafka, "Publica eventos em")
  Rel(ms_billing, kafka, "Publica eventos em")

  Rel(kafka, ms_patients, "Consome eventos de")
  Rel(kafka, ms_procedures, "Consome eventos de")
  Rel(kafka, ms_billing, "Consome eventos de")

  Rel(ms_patients, db_mongo, "Atualiza em", "TCP")
  Rel(ms_procedures, db_mongo, "Atualiza em", "TCP")
  Rel(ms_billing, db_mongo, "Atualiza em", "TCP")

  Rel(rag_api, db_weaviate, "Busca em", "TCP")
```

## Diagrama de Sequência - Criação de Paciente

Este diagrama de sequência ilustra o fluxo de criação de um novo paciente.

```mermaid
sequenceDiagram
  participant Usuário
  participant API Gateway
  participant MS Patients
  participant Kafka
  participant MS Audit

  Usuário->>API Gateway: POST /api/patients
  API Gateway->>MS Patients: POST /patients
  MS Patients->>MS Patients: Valida dados
  MS Patients->>MS Patients: Salva no PostgreSQL
  MS Patients-->>API Gateway: 201 Created
  API Gateway-->>Usuário: 201 Created

  MS Patients->>Kafka: Publica evento "patient_created"
  Kafka-->>MS Audit: Consome evento "patient_created"
  MS Audit->>MS Audit: Salva log de auditoria
```


