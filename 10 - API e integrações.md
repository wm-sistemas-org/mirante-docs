# API e integrações

[[00 - Início|Início]] · [[02 - Arquitetura e stack|Arquitetura e stack]] · [[11 - Auditoria, observabilidade e testes|Auditoria, observabilidade e testes]]

## API pública

O padrão é REST, versionado inicialmente em /api/v1, com documentação OpenAPI/Swagger. Exemplos de formato: GET /api/v1/customers, POST /api/v1/customers e PATCH /api/v1/customers/:id.

Antes dos módulos operacionais, devem ser definidos padrões consistentes para respostas, erros, códigos HTTP, paginação, filtros, ordenação e validação. Autenticação e autorização seguem as notas responsáveis.

GraphQL não faz parte da arquitetura inicial. Poderá ser avaliado futuramente para consultas complexas ou composição de dados se houver necessidade real.

## Identificadores

As principais entidades persistentes utilizam UUID v7 como identificador técnico, favorecendo geração distribuída e ordenação temporal e evitando dependência de sequência central. Isso também permite geração local no futuro offline.

Números amigáveis servem à operação humana, pesquisa, atendimento e documentos, sem substituir o UUID. Sua geração será definida por domínio. Produtos seguem a regra de SKU em [[08 - Produtos e variações|Produtos e variações]]; a numeração de vendas está pendente.

## Idempotência

Operações críticas ou sujeitas a repetição devem impedir duplicidade quando aplicável, especialmente pagamentos, finalização de vendas, fiscal, webhooks, integrações e sincronização offline.

O mecanismo de chave, escopo, validade e armazenamento ainda será definido. As garantias de estoque estão em [[09 - Estoque|Estoque]].

## Contratos internos e adapters

Módulos de negócio não devem conhecer SDKs, endpoints, modelos ou detalhes dos provedores externos. Integrações utilizam contratos internos e adapters/providers, traduzindo o modelo externo para o domínio do ERP.

Por exemplo, seller_sku de um provedor é traduzido para o conceito interno correspondente. Essa separação evita contaminar o domínio com convenções externas.

Integrações respeitam tenant e empresa. Credenciais não são hardcoded, expostas ao frontend ou registradas em logs e devem ser armazenadas de forma segura.

## Redis, BullMQ e processamento assíncrono

Redis e BullMQ são tecnologias aprovadas para necessidades futuras, sem implantação automática na fundação.

- Redis pode fornecer cache e suporte ao BullMQ.
- BullMQ pode executar filas, workers, retries e jobs.
- PostgreSQL permanece a fonte oficial de dados.
- Operações rápidas que exigem resposta imediata podem ser síncronas.
- Operações demoradas, externas ou sujeitas a retry devem considerar processamento assíncrono.

Exemplos futuros: emissão fiscal, marketplaces, e-mail, WhatsApp, importações, relatórios pesados e conciliação. Recuperação de senha já exige um mecanismo de e-mail na V0, mas não determina por si só a adoção de filas.

A política de retry será definida por integração. Intervalos como 1, 5 e 15 minutos e 1 hora são exemplos, não uma política aprovada para todos os casos.

## Webhooks e rastreabilidade

Webhooks precisam de autenticação, assinatura, validação, proteção contra replay e idempotência conforme o provedor.

Cada operação de integração deve ser identificável por empresa, provedor, horário, tentativa, resultado, erro, correlation ID e identificadores internos/externos.

## Limites e pendências

Integrações avançadas não fazem parte do piloto, conforme [[01 - Visão e escopo|Visão e escopo]]. Permanecem pendentes os contratos concretos, padrões de API, políticas de retry, idempotência, armazenamento de credenciais e entrega durável dos eventos.

---

[[09 - Estoque|← Anterior]] · [[11 - Auditoria, observabilidade e testes|Próxima →]]
