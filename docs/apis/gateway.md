# API Gateway

O API Gateway é o ponto de entrada único para todas as requisições externas ao sistema Lazarus. Ele é responsável por roteamento, autenticação, rate limiting, monitoramento e segurança.

## Visão Geral

- **Tecnologia**: Kong Gateway + Nginx
- **URL Base**: `https://api.lazarus.com`
- **Autenticação**: JWT (JSON Web Tokens)
- **Rate Limiting**: Sim

## Endpoints

O API Gateway roteia as requisições para os microsserviços correspondentes. A seguir, uma visão geral das rotas disponíveis:

| Rota Base | Microsserviço | Descrição |
|---|---|---|
| `/api/patients` | MS Patients | Gestão de pacientes |
| `/api/procedures` | MS Procedures | Gestão de procedimentos |
| `/api/billing` | MS Billing | Gestão de faturamento |
| `/api/audit` | MS Audit | Auditoria e logs |
| `/api/rag` | RAG API | Chat com IA e busca semântica |
| `/camunda` | Camunda | Motor de workflows |

Para detalhes sobre os endpoints de cada microsserviço, consulte a documentação específica de cada um.

## Autenticação

Todas as requisições para rotas protegidas devem incluir um token JWT no header `Authorization`:

```http
Authorization: Bearer <seu-token-jwt>
```

Para obter um token, utilize o endpoint de login do RAG API:

`POST /api/rag/auth/login`

## Rate Limiting

O API Gateway implementa rate limiting para proteger o sistema contra abuso. Os limites são:

- **Geral**: 1000 requisições por minuto
- **Autenticação**: 60 requisições por minuto
- **Uploads**: 10 requisições por minuto

Se o limite for excedido, a API retornará o código de status `429 Too Many Requests`.

## Códigos de Erro

O API Gateway pode retornar os seguintes códigos de erro:

| Código | Descrição |
|---|---|
| `400 Bad Request` | Requisição malformada |
| `401 Unauthorized` | Token de autenticação inválido ou ausente |
| `403 Forbidden` | Acesso negado ao recurso |
| `404 Not Found` | Rota não encontrada |
| `429 Too Many Requests` | Limite de requisições excedido |
| `500 Internal Server Error` | Erro interno no gateway |
| `502 Bad Gateway` | Erro de comunicação com o microsserviço |
| `503 Service Unavailable` | Microsserviço indisponível |
| `504 Gateway Timeout` | Timeout na comunicação com o microsserviço |


