# Tenants, empresas e acesso

[[00 - Início|Início]] · [[03 - Plataforma e revendedores|Plataforma e revendedores]] · [[05 - Autenticação e segurança|Autenticação e segurança]]

## Tenant e empresa

Tenant representa o grupo ou cliente contratante e é a fronteira principal de isolamento. Cada CNPJ dentro dele é uma empresa independente, mesmo quando juridicamente matriz ou filial.

Não existe uma camada obrigatória de filial. Unidades sem CNPJ poderão ser tratadas futuramente como outro conceito.

## Tipos de conta

O e-mail é único na plataforma. Na V0, cada conta possui somente um tipo de acesso.

| Tipo | Vínculo e alcance |
|---|---|
| Administrador WM | Plataforma e painel geral |
| Administrador do revendedor | Um revendedor e seus próprios clientes |
| Usuário operacional | Um único tenant e suas empresas autorizadas |

Usuário operacional não acessa múltiplos tenants. Contas administrativas não precisam de tenants artificiais. Usuários são cadastros independentes de [[07 - Pessoas|Pessoas]], sem vínculo com funcionários nesta etapa.

## Empresa ativa por aba

Cada aba pode operar em uma empresa diferente. Trocar a empresa em uma aba não altera as demais. A interface identifica claramente a empresa selecionada.

O backend valida o contexto autenticado, o tenant, o acesso à empresa e as permissões em cada requisição. Identificadores enviados pelo frontend não são confiáveis por si só.

## Acesso às empresas

Há duas formas de concessão:

- Empresas selecionadas: somente as empresas explicitamente marcadas.
- Todas as empresas, inclusive futuras: inclui automaticamente novas empresas daquele tenant.

A concessão não elimina restrições de situação, módulos habilitados ou ações permitidas.

## Perfis e sobrescritas

O usuário possui um perfil padrão com permissões granulares por módulo e ação, por exemplo estoque.visualizar e estoque.ajustar.

Para cada permissão na empresa:

| Opção | Resolução |
|---|---|
| Herdar | Utilizar a permissão do perfil padrão |
| Permitir | Conceder aquela ação na empresa |
| Negar | Bloquear aquela ação na empresa |

Na ausência de concessão pelo perfil ou pela sobrescrita, a ação é bloqueada. Primeiro é necessário ter acesso à empresa: uma sobrescrita não concede esse vínculo.

A interface mostra claramente permissões herdadas e sobrescritas. O padrão definitivo de nomes e o catálogo de ações serão detalhados antes da implementação.

## Administração de acessos no tenant

O administrador do tenant é um usuário operacional com autorização para administrar usuários, perfis e acesso às empresas do próprio tenant. Não é um quarto tipo de conta.

A função pode ser delegada, mas ninguém pode conceder acessos além do que está autorizado a administrar.

## Alterações de acesso

Mudanças de permissão ou remoção de acesso passam a valer na próxima requisição ao backend, sem exigir logout. Uma tela pode continuar exibindo dados já carregados, mas consultas e ações seguintes devem respeitar a nova configuração.

Bloqueios administrativos seguem [[03 - Plataforma e revendedores|Plataforma e revendedores]].

## Pendências

- Catálogo de permissões e limites detalhados de delegação.
- Comportamento de operações em andamento diante de alteração de acesso.
- Implementação técnica da atualização de permissões por requisição.

---

[[03 - Plataforma e revendedores|← Anterior]] · [[05 - Autenticação e segurança|Próxima →]]
