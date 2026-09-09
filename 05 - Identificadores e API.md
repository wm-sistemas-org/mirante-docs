# Identificadores e API

[[README|Início]] · [[04 - Autenticação e permissões|Anterior]] · [[06 - Segurança e auditoria|Próxima]]

> Conteúdo do documento mestre original. Seções: 11, 14. A numeração original foi preservada para rastreabilidade.

---

# 11. Estratégia de IDs

As principais entidades persistentes utilizarão:

> UUID v7.

UUID v7 será utilizado como identificador técnico.

Motivos:

* geração distribuída;
* suporte futuro ao offline;
* integrações;
* filas;
* menor risco de colisões;
* ordenação temporal melhor que UUID v4;
* não depender de sequência central.

Quando houver necessidade de identificação humana, será utilizado também:

> número ou código amigável.

Exemplo:

```text
ID técnico:
019c8d52-...

Número da venda:
15482
```

O UUID continuará sendo o identificador técnico principal.

O número amigável será utilizado para:

* interface;
* pesquisa;
* atendimento;
* documentos;
* operação humana.

A forma de geração dos números amigáveis será definida posteriormente por módulo/domínio.

---

# 14. API

O padrão oficial será:

> REST API.

A API será versionada.

Inicialmente:

```text
/api/v1
```

Exemplos:

```text
GET    /api/v1/customers
POST   /api/v1/customers
GET    /api/v1/customers/:id
PATCH  /api/v1/customers/:id
```

Serão definidos padrões consistentes para:

* endpoints;
* respostas;
* erros;
* códigos HTTP;
* paginação;
* filtros;
* ordenação.

A documentação da API será feita através de:

> OpenAPI / Swagger.

GraphQL não fará parte da arquitetura inicial.

Poderá ser avaliado futuramente caso exista necessidade real, por exemplo:

* dashboards;
* consultas complexas;
* composição de muitos dados;
* redução de múltiplas requisições.

REST continuará sendo o padrão principal.

## Idempotência

Operações críticas ou sujeitas a repetição deverão suportar idempotência quando necessário.

Principalmente:

* pagamentos;
* fiscal;
* integrações;
* webhooks;
* sincronização offline.

---

---

[[README|Início]] · [[04 - Autenticação e permissões|Anterior]] · [[06 - Segurança e auditoria|Próxima]]
