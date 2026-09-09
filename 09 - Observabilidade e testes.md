# Observabilidade e testes

[[README|Início]] · [[08 - PDV offline|Anterior]] · [[10 - Desenvolvimento e documentação|Próxima]]

> Conteúdo do documento mestre original. Seções: 18, 19. A numeração original foi preservada para rastreabilidade.

---

# 18. Observabilidade

O ERP deverá possuir observabilidade estruturada.

## Logs estruturados

Evitar logs como:

```text
entrou aqui
deu erro
```

Os logs deverão possuir contexto.

Exemplo:

```text
level
message
tenant
empresa
módulo
provider
requestId
timestamp
```

## Logs técnicos ≠ auditoria

Logs técnicos serão utilizados para:

* diagnóstico;
* erros;
* integrações;
* infraestrutura.

Auditoria será utilizada para:

* ações de negócio;
* rastreabilidade.

## Request ID / Correlation ID

Cada requisição deverá possuir um identificador.

Esse identificador deverá permitir correlacionar:

```text
Frontend
   ↓
Backend
   ↓
Módulo
   ↓
Fila
   ↓
Integração
```

Isso permitirá rastrear uma operação completa.

## Erros centralizados

Erros deverão seguir padrão.

Exemplos:

* VALIDATION_ERROR;
* ACCESS_DENIED;
* INTEGRATION_TIMEOUT;
* DATABASE_ERROR;
* INTERNAL_ERROR.

Stack traces não deverão ser enviados ao usuário final.

O usuário poderá receber um código de referência para suporte.

## Métricas

A arquitetura deverá permitir futuramente métricas como:

* tempo de resposta;
* erros;
* CPU;
* memória;
* conexões;
* filas;
* jobs;
* falhas de integrações.

## Health checks

O sistema deverá oferecer mecanismo para verificar saúde de componentes.

Exemplo:

```text
API: OK
PostgreSQL: OK
Redis: OK
```

## Monitoramento

Ferramentas específicas como:

* Sentry;
* Grafana;
* OpenTelemetry;
* Datadog;

não estão decididas ainda.

A decisão atual é o padrão de observabilidade, não o fornecedor.

---

# 19. Estratégia de testes

Testes automatizados farão parte obrigatória do desenvolvimento.

Serão utilizados conforme necessidade:

* testes unitários;
* testes de integração;
* testes E2E;
* testes de contrato.

## Áreas críticas

As seguintes áreas deverão possuir forte cobertura automatizada:

* multi-tenancy;
* autenticação;
* autorização;
* permissões;
* financeiro;
* fiscal;
* estoque;
* idempotência;
* integrações críticas;
* cancelamentos;
* regras de negócio sensíveis.

## Testes multi-tenant

Deverão existir testes que garantam que:

> Tenant A nunca consiga acessar dados do Tenant B.

Também deverão existir testes para permissões entre empresas do mesmo tenant.

## Correções de bugs

Correções de bugs deverão, sempre que possível, incluir teste de regressão reproduzindo o problema.

## Cobertura

Cobertura percentual será utilizada como indicador.

Não deverá ser tratada como objetivo isolado.

É preferível possuir boa cobertura de regras críticas do que gerar testes irrelevantes apenas para atingir porcentagem.

## Definition of Done

Quando aplicável, uma tarefa só será considerada concluída quando:

* implementação estiver pronta;
* lint passar;
* build passar;
* testes existentes passarem;
* novos testes necessários forem adicionados;
* documentação estiver atualizada;
* regras arquiteturais forem respeitadas;
* Pull Request for revisado.

---

---

[[README|Início]] · [[08 - PDV offline|Anterior]] · [[10 - Desenvolvimento e documentação|Próxima]]
