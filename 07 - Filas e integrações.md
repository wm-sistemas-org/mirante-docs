# Filas e integrações

[[README|Início]] · [[06 - Segurança e auditoria|Anterior]] · [[08 - PDV offline|Próxima]]

> Conteúdo do documento mestre original. Seções: 13, 16. A numeração original foi preservada para rastreabilidade.

---

# 13. Cache, filas e jobs

Tecnologias escolhidas:

* Redis;
* BullMQ.

Porém não serão implementadas imediatamente.

Serão introduzidas quando surgirem necessidades reais.

## Redis

Poderá ser utilizado para:

* cache;
* suporte ao BullMQ.

Cache nunca será fonte oficial de verdade.

PostgreSQL continuará sendo a fonte oficial.

## BullMQ

Poderá ser utilizado para:

* filas;
* workers;
* retries;
* jobs;
* tarefas agendadas.

Exemplos futuros:

* emissão fiscal;
* sincronização de marketplace;
* envio de e-mail;
* WhatsApp;
* importações;
* relatórios pesados;
* conciliação;
* integrações externas.

## Princípio

Se a operação for rápida e exigir resposta imediata:

> síncrono.

Se for demorada, externa, sujeita a retry ou independente da resposta imediata:

> considerar processamento assíncrono.

---

# 16. Integrações externas

O ERP terá muitas integrações no futuro.

Exemplos:

* marketplaces;
* gateways;
* Open Finance;
* bancos;
* fiscal;
* SEFAZ;
* WhatsApp;
* serviços externos.

Por isso será criada uma arquitetura padronizada de integrações.

## Princípio

Módulos de negócio não deverão conhecer diretamente:

* SDKs externos;
* endpoints externos;
* modelos externos;
* detalhes específicos dos providers.

Será utilizada uma camada de:

> contratos internos + adapters/providers.

Exemplo:

```text
ERP
 ↓
MarketplaceProvider
 ↓
MercadoLivreProvider
```

Outro marketplace poderá implementar o mesmo contrato.

## Anti-Corruption Layer

Modelos externos não devem contaminar o domínio interno.

Exemplo:

```text
API externa:
seller_sku

ERP:
productCode
```

O adapter será responsável pela tradução.

## Integrações assíncronas

Quando possível, integrações externas devem ser processadas de forma assíncrona.

Exemplo:

```text
Usuário salva produto
       ↓
ERP salva no PostgreSQL
       ↓
fila de integração
       ↓
worker
       ↓
marketplace
```

## Retry

Falhas externas deverão poder ser repetidas automaticamente.

Exemplo:

```text
1 minuto
5 minutos
15 minutos
1 hora
```

A política exata será definida posteriormente.

## Idempotência

Integrações críticas deverão ser idempotentes para evitar duplicidade.

## Webhooks

Webhooks deverão ser tratados com:

* autenticação;
* assinatura;
* validação;
* proteção contra replay;
* idempotência.

## Credenciais

Credenciais externas:

* nunca ficarão hardcoded;
* nunca serão expostas ao frontend;
* deverão ser armazenadas de forma segura.

As integrações deverão respeitar contexto de:

* tenant;
* empresa.

## Observabilidade das integrações

Será necessário identificar:

* operação;
* empresa;
* provider;
* horário;
* tentativa;
* resultado;
* erro;
* correlation ID;
* identificadores internos e externos.

---

---

[[README|Início]] · [[06 - Segurança e auditoria|Anterior]] · [[08 - PDV offline|Próxima]]
