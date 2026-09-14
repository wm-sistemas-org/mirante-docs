# Domínios e propriedade dos dados

[[00 - Início|Início]] · [[02 - Arquitetura e stack|Arquitetura e stack]] · [[07 - Pessoas|Pessoas]] · [[08 - Produtos e variações|Produtos e variações]] · [[09 - Estoque|Estoque]]

## Fronteiras dos módulos

| Módulo | Responsabilidade |
|---|---|
| Identidade | Login, senhas e sessões |
| Administração da plataforma | Revendedores, tenants, empresas e módulos habilitados |
| White label | Marca e configuração visual |
| Controle de acesso | Perfis, permissões e acesso às empresas |
| Auditoria | Registro das ações auditáveis |
| Pessoas | Cadastros e papéis de cliente, fornecedor, transportador e funcionário |
| Catálogo | Produtos, variações, categorias e unidades |
| Estoque | Saldos e movimentações |
| Vendas | Vendas, itens, trocas e devoluções |
| Financeiro | Contas a pagar e receber, pagamentos e recebimentos |
| Caixa | Abertura, movimentações e fechamento por operador |

São fronteiras internas de um monólito. Compras e verticais especializadas serão adicionadas posteriormente, sem duplicar conceitos do núcleo.

## Propriedade e escopo dos dados

| Dado | Escopo |
|---|---|
| Usuário operacional | Um tenant; sem vínculo com pessoa |
| Pessoa e seus papéis | Empresa; criação em outras empresas gera cadastros independentes |
| Produto, variação, categoria e unidade | Tenant no modo compartilhado; empresa no modo separado |
| Preço e habilitação de comercialização | Empresa |
| Controle, saldo e movimentação de estoque | Empresa |
| Venda, títulos financeiros e caixa | Empresa |

As regras de identidade e visibilidade de pessoas estão em [[07 - Pessoas|Pessoas]]. Os dois modos de catálogo estão em [[08 - Produtos e variações|Produtos e variações]]. Compartilhar catálogo não compartilha saldos ou operações.

## Colaboração aprovada

- Vendas consulta Pessoas e Catálogo por contratos públicos.
- Estoque é o único responsável por registrar movimentações e controlar saldos.
- Financeiro é responsável pelos títulos, pagamentos e recebimentos.
- Caixa controla as sessões dos operadores e vincula suas movimentações aos registros financeiros, evitando duplicar recebimentos.
- Vendas coordena a finalização e solicita os efeitos em Estoque e Financeiro.
- Vendas conduz trocas e devoluções; cada módulo responsável executa seus efeitos.

Nenhum módulo acessa a persistência interna de outro. Contratos, eventos e transações devem respeitar [[02 - Arquitetura e stack|Arquitetura e stack]].

## Modelagem e pendências

As responsabilidades acima estão aprovadas. Ainda precisam ser definidos os contratos concretos, entidades e relacionamentos técnicos, eventos, dependências detalhadas e mecanismo de coordenação transacional.

A modelagem do banco deve seguir essas fronteiras. As regras de vendas, financeiro e caixa serão aprofundadas antes de implementar seus fluxos; a aprovação do escopo não define automaticamente todos os comportamentos.

---

[[05 - Autenticação e segurança|← Anterior]] · [[07 - Pessoas|Próxima →]]
