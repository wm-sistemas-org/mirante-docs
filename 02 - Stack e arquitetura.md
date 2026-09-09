# Stack e arquitetura

[[README|Início]] · [[01 - Visão e princípios|Anterior]] · [[03 - White label e multi-tenancy|Próxima]]

> Conteúdo do documento mestre original. Seções: 3, 4, 5. A numeração original foi preservada para rastreabilidade.

---

# 3. Stack principal

A stack definida inicialmente é:

## Backend

* NestJS;
* TypeScript.

## Frontend

* Next.js;
* React;
* TypeScript.

O Next.js será utilizado como framework principal do frontend baseado em React.

## Banco de dados

* PostgreSQL.

## ORM

* Prisma ORM.

## Cache, filas e jobs

Tecnologias definidas:

* Redis;
* BullMQ.

Porém, Redis e BullMQ **não serão utilizados imediatamente na primeira etapa do desenvolvimento**.

O foco inicial será construir o núcleo funcional do ERP.

Redis e BullMQ serão introduzidos posteriormente quando surgirem necessidades concretas de:

* cache;
* filas;
* processamento assíncrono;
* retries;
* workers;
* jobs agendados;
* integrações externas;
* tarefas demoradas.

O PostgreSQL continuará sendo a fonte oficial dos dados.

Redis será utilizado apenas como infraestrutura auxiliar.

---

# 4. Arquitetura do backend

A arquitetura escolhida será:

> **Monólito Modular.**

O sistema continuará sendo uma única aplicação backend implantável, porém dividido internamente em módulos com fronteiras claras.

Exemplos de possíveis módulos:

* vendas;
* estoque;
* financeiro;
* fiscal;
* compras;
* autenticação;
* usuários;
* empresas;
* integrações;
* configurações.

Cada módulo deverá possuir responsabilidade bem definida.

## Regras de modularidade

Um módulo não poderá acessar diretamente:

* repository interno de outro módulo;
* implementação interna de outro módulo;
* tabelas pertencentes logicamente a outro módulo;
* services internos não expostos.

Os módulos devem se comunicar através de:

### 1. Contratos públicos síncronos

Quando for necessária resposta imediata.

Exemplo:

Vendas precisa consultar disponibilidade de estoque.

### 2. Eventos internos

Quando um módulo apenas precisa informar que algo aconteceu.

Exemplo:

Venda finalizada.

Outros módulos podem reagir:

* estoque;
* financeiro;
* fiscal;
* BI.

### 3. Filas

Quando houver:

* processamento demorado;
* integração externa;
* retry;
* processamento assíncrono.

Redis + BullMQ serão utilizados quando essa necessidade surgir.

## Regra arquitetural

> Nenhum módulo deve acessar diretamente a persistência ou implementação interna de outro módulo.

Os módulos devem ser desenvolvidos com fronteiras suficientemente claras para que, no futuro, algum módulo possa ser extraído para um serviço independente caso exista uma necessidade real.

Isso não significa implementar microsserviços agora.

---

# 5. Arquitetura geral do sistema

A visão macro inicial é:

```text
Frontend Next.js / React
          │
          │
          ▼
Backend NestJS
Monólito Modular
          │
          ▼
Camada de persistência
Prisma ORM
          │
          ▼
PostgreSQL
```

Integrações externas também deverão passar pelo backend ou por workers controlados pela aplicação.

Integrações externas nunca deverão acessar diretamente o banco de dados.

---

---

[[README|Início]] · [[01 - Visão e princípios|Anterior]] · [[03 - White label e multi-tenancy|Próxima]]
