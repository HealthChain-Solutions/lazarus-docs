# Problemas Comuns

Esta seção descreve problemas comuns que podem ocorrer ao trabalhar com o sistema Lazarus e como resolvê-los.

## Microsserviço não inicia

- **Sintoma**: O microsserviço falha ao iniciar, geralmente com um erro no console.
- **Causa Comum**: Variáveis de ambiente ausentes ou incorretas.
- **Solução**: Verifique se o arquivo `.env` do microsserviço está correto e completo. Compare com o `.env.example` para garantir que todas as variáveis estão presentes.

## Erro de conexão com o banco de dados

- **Sintoma**: O microsserviço não consegue se conectar ao banco de dados (PostgreSQL, MongoDB ou Redis).
- **Causa Comum**: O banco de dados não está em execução ou as credenciais estão incorretas.
- **Solução**: Verifique se os contêineres do Docker dos bancos de dados estão em execução. Verifique as variáveis de ambiente de conexão com o banco de dados no arquivo `.env`.

## Eventos do Kafka não são processados

- **Sintoma**: Um microsserviço publica um evento no Kafka, mas o consumidor não o processa.
- **Causa Comum**: O consumidor não está em execução, o tópico está incorreto ou há um erro no processamento do evento.
- **Solução**: Verifique se o microsserviço consumidor está em execução. Verifique os logs do consumidor para ver se há erros. Utilize o Kafka UI para inspecionar as mensagens no tópico e na dead letter queue.

## Erro 502 Bad Gateway no API Gateway

- **Sintoma**: O API Gateway retorna o código de status `502 Bad Gateway`.
- **Causa Comum**: O microsserviço de destino não está em execução ou está inacessível.
- **Solução**: Verifique se o microsserviço de destino está em execução e saudável. Verifique os logs do API Gateway e do microsserviço para mais detalhes.

## Erro 401 Unauthorized no API Gateway

- **Sintoma**: O API Gateway retorna o código de status `401 Unauthorized`.
- **Causa Comum**: O token JWT está ausente, inválido ou expirado.
- **Solução**: Verifique se o token JWT está sendo enviado corretamente no header `Authorization`. Obtenha um novo token se o endpoint de login, se necessário.


