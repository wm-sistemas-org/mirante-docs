# Arquitetura e stack

[[00 - Início|Início]] · [[06 - Domínios e propriedade dos dados|Domínios e propriedade dos dados]] · [[10 - API e integrações|API e integrações]]

## Stack aprovada

| Camada | Tecnologia |
|---|---|
| Backend | NestJS e TypeScript |
| Frontend | Next.js, React e TypeScript |
| Persistência | Prisma ORM |
| Banco | PostgreSQL |
| Infraestrutura auxiliar futura | Redis e BullMQ, quando houver necessidade |

PostgreSQL é a fonte oficial dos dados. Cache e filas não substituem a persistência de negócio. Critérios de introdução de Redis e BullMQ estão em [[10 - API e integrações|API e integrações]].

## Monólito modular

O backend é uma única aplicação implantável, dividida em módulos com responsabilidades e fronteiras claras. A divisão aprovada está em [[06 - Domínios e propriedade dos dados|Domínios e propriedade dos dados]].

Um módulo não acessa diretamente repositórios, tabelas, serviços não expostos ou implementações internas de outro módulo.

A comunicação ocorre por:

- Contratos públicos síncronos quando há necessidade de resposta imediata.
- Eventos internos para comunicar fatos.
- Filas quando houver necessidade concreta de processamento assíncrono, integração, tarefas demoradas ou retry.

Eventos internos não definem, por si só, as garantias de entrega ou de transação. O mecanismo de coordenação transacional ainda será detalhado; deve cumprir as garantias já aprovadas em [[09 - Estoque|Estoque]].

As fronteiras devem permitir eventual extração de um módulo quando houver motivo real. Microsserviços não fazem parte da arquitetura inicial.

## Fluxo macro

Frontend Next.js/React → backend NestJS → persistência Prisma → PostgreSQL.

Integrações passam pelo backend ou por workers controlados pela aplicação. Serviços externos não acessam diretamente o banco.

O frontend terá organização compatível com os domínios e contexto de marca, empresa, permissões, navegação e tratamento de erros. Não serão criadas antecipadamente telas vazias para módulos futuros.

## Persistência e isolamento

O banco é compartilhado, com isolamento lógico por tenant na aplicação e persistência. PostgreSQL RLS não será utilizado inicialmente; poderá ser avaliado como defesa adicional.

Os escopos de dados e de autorização estão em [[06 - Domínios e propriedade dos dados|Domínios e propriedade dos dados]] e [[04 - Tenants, empresas e acesso|Tenants, empresas e acesso]].

## Pendências técnicas

Estrutura interna de pastas, schema Prisma, migrations, implementação dos contratos, versões das dependências e coordenação de transações serão definidos na documentação técnica dos repositórios, respeitando as decisões gerais.

---

[[01 - Visão e escopo|← Anterior]] · [[03 - Plataforma e revendedores|Próxima →]]
