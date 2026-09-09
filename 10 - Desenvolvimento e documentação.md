# Desenvolvimento e documentação

[[README|Início]] · [[09 - Observabilidade e testes|Anterior]] · [[11 - Decisões futuras e continuidade|Próxima]]

> Conteúdo do documento mestre original. Seções: 20, 21, 22, 23. A numeração original foi preservada para rastreabilidade.

---

# 20. Git e fluxo de trabalho

O projeto será dividido inicialmente em três repositórios principais.

## Repositório 1 — Documentação Geral

Exemplo:

```text
mirante-erp-docs
```

Contém:

* visão do produto;
* arquitetura;
* decisões;
* ADRs;
* multi-tenancy;
* white label;
* segurança;
* autenticação;
* permissões;
* integrações;
* offline;
* observabilidade;
* testes;
* roadmap;
* regras gerais.

## Repositório 2 — Backend

Exemplo:

```text
mirante-erp-backend
```

Contém:

* código backend;
* documentação técnica do backend;
* arquitetura interna;
* módulos;
* Prisma;
* persistência;
* migrations;
* integrações;
* testes;
* API.

## Repositório 3 — Frontend

Exemplo:

```text
mirante-erp-frontend
```

Contém:

* código frontend;
* documentação técnica do frontend;
* design system;
* componentes;
* navegação;
* estado;
* padrões de interface;
* consumo da API;
* testes.

## Hierarquia documental

A documentação geral será a referência de decisões macro.

Backend e frontend deverão implementar essas decisões.

Caso seja necessário alterar uma decisão macro:

1. decisão deverá ser discutida;
2. ADR/documentação geral deverá ser atualizada;
3. backend/frontend deverão ser adaptados posteriormente.

## Desenvolvimento

O fluxo padrão será:

```text
Issue / Tarefa
      ↓
Responsável
Murilo ou Felipe
      ↓
Branch
      ↓
IA auxilia
      ↓
Implementação
      ↓
Testes
      ↓
Pull Request
      ↓
Revisão humana
      ↓
Merge
```

Desenvolvimento direto na branch principal deverá ser evitado.

## Branches

Sugestão de padrão:

```text
feat/...
fix/...
refactor/...
docs/...
```

## Commits

Poderá ser utilizado Conventional Commits.

Exemplos:

```text
feat:
fix:
refactor:
docs:
test:
chore:
```

---

# 21. Uso de IA no desenvolvimento

A IA será parte ativa do desenvolvimento.

Porém deverá respeitar regras formais.

## O que a IA pode decidir

A IA poderá tomar decisões locais de baixo impacto.

Exemplos:

* nomes de variáveis;
* pequenas funções;
* refactors locais;
* testes;
* implementação de tarefas já especificadas;
* melhoria de legibilidade;
* correções dentro do escopo.

## O que a IA NÃO pode decidir sozinha

A IA não poderá alterar sem aprovação:

* stack principal;
* arquitetura;
* multi-tenancy;
* autenticação;
* autorização;
* estratégia de IDs;
* contratos públicos;
* padrão de API;
* banco;
* ORM;
* arquitetura de integrações;
* divisão dos módulos;
* tecnologias estruturais.

## Mudanças arquiteturais

Mudanças importantes deverão ser propostas antes da implementação.

Fluxo:

```text
IA identifica necessidade
        ↓
propõe
        ↓
Murilo/Felipe avaliam
        ↓
ADR
        ↓
aprovação
        ↓
implementação
```

## Escopo

A IA deverá trabalhar apenas dentro do escopo da tarefa.

Exemplo:

Se a tarefa for:

> corrigir bug do estoque

ela não deverá aproveitar para:

* refatorar autenticação;
* reorganizar vários módulos;
* trocar bibliotecas;
* renomear dezenas de arquivos;
* alterar arquitetura.

Caso encontre outro problema, deverá registrar como sugestão ou tarefa separada.

## Código gerado por IA

Código gerado por IA não será automaticamente aceito.

Deverá passar pelos mesmos processos:

* lint;
* build;
* testes;
* Pull Request;
* revisão humana.

## Documentos obrigatórios

Antes de trabalhar no projeto, a IA deverá consultar:

* documentação geral;
* ADRs;
* regras arquiteturais;
* README;
* CONTRIBUTING;
* AI_RULES;
* documentação específica do repositório.

---

# 22. Qualidade e legibilidade do código

Princípio:

> O código deve ser escrito para humanos primeiro e para máquinas depois.

A IA deverá priorizar:

* legibilidade;
* simplicidade;
* previsibilidade;
* consistência;
* manutenção.

## Padrões de projeto

Padrões de projeto deverão ser utilizados quando resolverem problemas reais.

Exemplos:

* Adapter;
* Strategy;
* Factory;
* Repository;
* Observer.

Porém não deverão ser utilizados apenas para tornar o código aparentemente sofisticado.

Evitar:

* abstrações desnecessárias;
* interfaces sem necessidade;
* excesso de camadas;
* overengineering;
* generalizações prematuras.

Regra:

> Antes de criar uma nova abstração, avaliar se existe uma necessidade real e se o problema justifica essa abstração.

## Comentários

Preferir código autoexplicativo.

Comentários deverão explicar principalmente:

> por que algo existe.

Não comentar coisas óbvias.

### Exemplo ruim

```ts
// Declara a variável total
const total = calculateTotal(items);

// Verifica se o total é maior que zero
if (total > 0) {
  // Retorna total
  return total;
}
```

Esses comentários são proibitivos/desnecessários.

### Exemplo válido

```ts
// O estoque não é bloqueado neste momento porque vendas offline
// podem ser sincronizadas posteriormente e serão reconciliadas.
```

Comentários são apropriados quando houver:

* regra de negócio não óbvia;
* decisão técnica relevante;
* workaround;
* comportamento inesperado;
* limitação externa;
* motivo arquitetural.

## Outras regras

Evitar:

* funções gigantes;
* classes gigantes;
* nomes genéricos;
* `any` sem justificativa;
* magic numbers;
* magic strings;
* código morto;
* TODO sem contexto;
* duplicação significativa;
* abstração criada apenas para possível uso futuro.

SOLID deve ser utilizado como orientação, e não como dogma.

---

# 23. Documentação

Documentação será tratada como parte oficial do projeto.

A intenção inicial é utilizar:

* Markdown;
* Git;
* possivelmente Obsidian como interface de edição.

Os arquivos deverão permanecer em formatos simples e legíveis por:

* humanos;
* Git;
* agentes de IA.

A documentação deverá evitar duplicação.

## Regra de autoridade

A documentação geral define:

> o que o sistema é e quais decisões macro ele segue.

Backend define:

> como o backend implementa essas decisões.

Frontend define:

> como o frontend implementa essas decisões.

---

---

[[README|Início]] · [[09 - Observabilidade e testes|Anterior]] · [[11 - Decisões futuras e continuidade|Próxima]]
