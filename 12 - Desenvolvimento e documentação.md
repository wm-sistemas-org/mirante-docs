# Desenvolvimento e documentação

[[00 - Início|Início]] · [[02 - Arquitetura e stack|Arquitetura e stack]] · [[13 - Evolução e pendências|Evolução e pendências]]

## Repositórios e autoridade

| Repositório | Responsabilidade |
|---|---|
| mirante-docs | Documentação geral: produto, regras, arquitetura e decisões |
| Backend, nome previsto mirante-erp-backend | Implementação, módulos, Prisma, migrations, contratos e testes técnicos |
| Frontend, nome previsto mirante-erp-frontend | Implementação de interface, componentes, navegação, estado e consumo da API |

O repositório geral é [mirante-docs](https://github.com/wm-sistemas-org/mirante-docs).

A documentação geral define o que o sistema é. Backend e frontend documentam como implementam essas decisões. Detalhes de tabelas, classes e pastas pertencem aos repositórios técnicos.

## Fluxo de trabalho

Tarefa → responsável (Murilo ou Felipe) → branch → implementação com apoio de IA → testes → pull request → revisão humana → merge.

Desenvolvimento direto na branch principal deve ser evitado. Prefixos sugeridos: feat/, fix/, refactor/ e docs/. Conventional Commits pode ser utilizado, com tipos como feat, fix, refactor, docs, test e chore.

## Preparação e execução das tarefas

Antes de implementar, definir proporcionalmente ao risco: objetivo, escopo, atores, regras, permissões, módulo responsável, entidades, impactos, erros, auditoria e critérios de aceite.

Priorizar pequenas funcionalidades completas, incluindo regra, persistência, backend, API, frontend e verificações. Não antecipar dezenas de tabelas, controllers ou telas sem processo funcional.

Detalhar as dependências necessárias à entrega atual, sem exigir especificação de todos os módulos futuros.

## Uso de IA

A IA pode decidir nomes de variáveis, pequenas funções, testes, refactors locais e correções dentro do escopo aprovado.

Mudanças estruturais em stack, arquitetura, tenancy, autenticação, autorização, IDs, contratos públicos, API, banco, ORM, integrações ou fronteiras de módulos exigem proposta e aprovação humana. Mudanças arquiteturais relevantes são registradas em ADR.

Antes de trabalhar, consultar documentação geral, ADRs, regras arquiteturais, README, CONTRIBUTING, AI_RULES e documentação específica do repositório, quando disponíveis. Essas referências não significam que todos esses arquivos já existem neste vault.

Não substituir decisões silenciosamente nem tratar sugestões como aprovadas. Problemas fora do escopo devem ser relatados como sugestões ou tarefas separadas.

Código gerado por IA passa pelos mesmos critérios de lint, build, testes e revisão humana.

## Legibilidade

Código é escrito para humanos primeiro. Priorizar simplicidade, previsibilidade e consistência.

Padrões como Adapter, Strategy, Factory, Repository e Observer só devem ser usados quando resolverem um problema real. SOLID orienta, sem impor abstrações desnecessárias.

Evitar funções e classes gigantes, nomes genéricos, any sem justificativa, números e strings mágicos, código morto, TODO sem contexto e duplicação significativa.

Comentários explicam motivos, regras não óbvias, limitações externas e workarounds. Não repetem o que o código já mostra nem introduzem regras de negócio ainda não aprovadas.

## Organização da documentação

Este vault usa Markdown, Git e links nativos do Obsidian. O índice é [[00 - Início|Início]].

Cada assunto possui uma fonte principal. Outras notas fazem referências em vez de duplicar regras. A redação descreve o comportamento vigente, sem reproduzir a sequência da conversa ou a numeração de blocos.

Notas de domínio explicam responsabilidade, regras, exemplos úteis, limites da V1 e pendências específicas. [[13 - Evolução e pendências|Evolução e pendências]] funciona como índice das decisões abertas.

Ao aprovar uma alteração, atualizar a nota responsável e verificar referências relacionadas. Regras superadas são removidas da documentação vigente; seu histórico permanece no Git.

ADRs registram decisões arquiteturais relevantes, contexto e motivo, sem exigir um documento separado para cada campo de cadastro. Um ADR não substitui a atualização da regra vigente.

## Limites de autoridade

A aprovação de um recurso no escopo não aprova todos os detalhes possíveis da implementação. Propostas, possibilidades futuras e pendências devem ser identificadas como tal.

Critérios de conclusão de tarefas estão em [[11 - Auditoria, observabilidade e testes|Auditoria, observabilidade e testes]].

---

[[11 - Auditoria, observabilidade e testes|← Anterior]] · [[13 - Evolução e pendências|Próxima →]]
