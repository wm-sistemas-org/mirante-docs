# White label e multi-tenancy

[[README|Início]] · [[02 - Stack e arquitetura|Anterior]] · [[04 - Autenticação e permissões|Próxima]]

> Conteúdo do documento mestre original. Seções: 6, 7, 8. A numeração original foi preservada para rastreabilidade.

---

# 6. White label e revendedores

O ERP terá suporte nativo a white label.

A hierarquia será aproximadamente:

```text
Plataforma
    ↓
Revendedor
    ↓
Tenant
    ↓
Empresas
```

Cada revendedor poderá possuir múltiplos clientes.

O revendedor poderá personalizar:

* nome da marca;
* logo;
* cores;
* favicon;
* e-mail;
* nome exibido em comunicações;
* identidade visual;
* subdomínio.

Inicialmente será utilizado o domínio principal:

```text
miranteerp.com.br
```

Cada revendedor poderá possuir algo como:

```text
revendedor.miranteerp.com.br
```

No futuro poderá ser permitido domínio próprio através de configuração de domínio/CNAME.

Exemplo:

```text
erp.revendedor.com.br
```

## Responsabilidades do revendedor

O revendedor poderá controlar:

* identidade visual;
* clientes;
* comercial;
* preço cobrado do cliente final;
* ativação de módulos permitidos;
* suporte de primeiro nível.

## Responsabilidades da plataforma

A plataforma continuará responsável por:

* infraestrutura;
* segurança;
* atualizações;
* arquitetura;
* versões;
* banco de dados;
* backups;
* módulos disponíveis;
* limites técnicos;
* integrações centrais;
* cobrança do revendedor;
* suporte técnico avançado.

## Modelo comercial

A plataforma cobrará do revendedor.

O revendedor terá liberdade para definir quanto cobrará do cliente final.

A cobrança da plataforma poderá considerar o número de empresas/CNPJs ativos.

O cliente final normalmente deverá procurar primeiro o revendedor para suporte.

Fluxo:

```text
Cliente final
     ↓
Revendedor
     ↓
Plataforma
```

O white label deverá ser baseado em configuração.

Não devem existir condições específicas espalhadas pelo código como:

```text
if revendedor == X
```

---

# 7. Multi-tenancy

Multi-tenancy será nativo desde o início.

## Definição de Tenant

Para o Mirante ERP:

> Tenant representa o grupo/cliente contratante do sistema.

Um tenant poderá possuir múltiplas empresas.

Exemplo:

```text
Tenant: Grupo Silva

├── Empresa A
├── Empresa B
└── Empresa C
```

## Empresa

Para fins do Mirante ERP:

> Cada CNPJ cadastrado dentro do tenant será tratado como uma Empresa independente.

Mesmo quando juridicamente um CNPJ for matriz ou filial de outro CNPJ, dentro do ERP ele será tratado como uma empresa independente.

Isso ocorre porque:

* cada CNPJ possui operação própria;
* permissões podem variar;
* configurações podem variar;
* fiscal pode variar;
* cobrança será realizada por CNPJ.

Portanto, a hierarquia principal será:

```text
Plataforma
    ↓
Revendedor
    ↓
Tenant / Grupo
    ↓
Empresas / CNPJs
```

Não haverá uma camada estrutural obrigatória chamada "filial" no modelo macro inicial.

Caso no futuro seja necessário representar unidades internas sem CNPJ, isso poderá ser tratado como outro conceito.

## Banco multi-tenant

Inicialmente será utilizado:

> PostgreSQL compartilhado com isolamento lógico por tenant.

Ou seja:

* um banco principal;
* os dados dos diferentes tenants compartilham a infraestrutura;
* o isolamento ocorre através do contexto do tenant.

O revendedor não será utilizado como chave principal de isolamento.

O isolamento principal será pelo tenant.

## Contexto do tenant

O frontend não poderá simplesmente informar livremente:

```text
tenantId = X
```

e ser considerado confiável.

O tenant deverá ser identificado a partir do contexto autenticado do usuário.

Toda operação deverá respeitar:

```text
Usuário
   ↓
Tenant
   ↓
Empresa ativa
   ↓
Permissões
   ↓
Operação
```

## PostgreSQL RLS

PostgreSQL Row Level Security não será utilizado inicialmente.

O isolamento será implementado inicialmente na camada da aplicação/persistência.

RLS poderá ser avaliado futuramente como camada adicional de defesa em profundidade.

---

# 8. Usuários e acesso

Cada usuário pertence a:

> um único tenant.

Um usuário **não poderá acessar múltiplos tenants**.

Dentro do tenant, porém, o usuário poderá receber acesso a:

* uma empresa;
* várias empresas;
* todas as empresas.

Exemplo:

```text
Tenant: Grupo Silva

Usuário X

✓ Empresa A
✓ Empresa B
✗ Empresa C
```

Após autenticação, o sistema disponibilizará apenas as empresas que aquele usuário pode acessar.

O usuário terá uma empresa ativa durante sua operação.

Ao trocar a empresa ativa, o backend deverá validar se ele possui acesso à empresa solicitada.

O frontend poderá solicitar a troca, porém a autorização será sempre validada pelo backend.

---

---

[[README|Início]] · [[02 - Stack e arquitetura|Anterior]] · [[04 - Autenticação e permissões|Próxima]]
