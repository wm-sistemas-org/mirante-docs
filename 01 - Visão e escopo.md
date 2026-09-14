# Visão e escopo

[[00 - Início|Início]] · [[02 - Arquitetura e stack|Arquitetura e stack]] · [[13 - Evolução e pendências|Evolução e pendências]]

## Objetivo e princípios

O Mirante ERP é um ERP web modular e white label, desenvolvido inicialmente por Murilo e Felipe. A plataforma deve crescer para atender diferentes segmentos sem perder legibilidade, segurança ou capacidade de manutenção.

Os princípios são: separação de responsabilidades, multi-tenancy e white label nativos, documentação, testes automatizados e evolução gradual. Complexidade arquitetural e operacional só deve ser introduzida quando houver necessidade concreta. A IA auxilia o desenvolvimento dentro das regras de [[12 - Desenvolvimento e documentação|Desenvolvimento e documentação]].

## Público e primeira entrega

A V1 será um piloto para varejo, inicialmente lojas de roupas e semijoias. A primeira entrega deve validar um fluxo operacional pequeno e completo sobre a arquitetura aprovada. Não representa uma promessa de atendimento a todos os segmentos.

A evolução inicial é: fundação técnica (V0), núcleo operacional para o piloto (V1), maturação e funcionalidades futuras. Datas e numeração das etapas posteriores ainda não estão definidas.

## V0 — Fundação técnica

A V0 inclui:

- Backend, frontend e persistência com a stack aprovada.
- Painel geral da WM e painel simples do revendedor.
- Cadastro e administração de revendedores, tenants, empresas e usuários.
- Atendimento direto pela WM, sem revendedor obrigatório.
- White label básico: nome, logo, cores, identificação e contexto do revendedor.
- Login, recuperação de senha, logout e revogação de sessões.
- Perfis, permissões granulares e sobrescritas por empresa.
- Contexto de empresa independente por aba.
- Auditoria, logs estruturados, correlação de requisições, erros centralizados e health checks.
- API REST documentada e testes da fundação.

### Critérios de conclusão da V0

O fluxo de configuração precisa permitir criar um revendedor, um tenant, duas empresas e usuários com acessos diferentes. Deve ser possível:

- Entrar, selecionar uma empresa autorizada e visualizar a marca correspondente.
- Executar uma ação permitida e bloquear uma ação proibida no backend.
- Impedir acesso a outra empresa não autorizada e a outro tenant.
- Alterar permissões e aplicar a alteração na próxima requisição.
- Executar logout, revogação de sessão e recuperação de senha.
- Consultar a auditoria de uma alteração administrativa.

A entrega também segue os critérios gerais de [[11 - Auditoria, observabilidade e testes|Auditoria, observabilidade e testes]].

## V1 — Núcleo operacional do piloto

| Área | Escopo aprovado |
|---|---|
| Pessoas | Clientes, fornecedores, transportadores e funcionários, com pesquisa, edição e inativação |
| Catálogo | Produtos simples e com variações, categorias, unidades, SKU, código de barras opcional e preço por empresa |
| Estoque | Saldo inicial, entradas, saídas, ajustes e histórico por empresa |
| Vendas | Criação, itens, identificação de cliente, desconto, finalização, consulta e cancelamento |
| Pagamentos | Mais de uma forma na mesma venda; registro manual, sem integração de confirmação |
| Financeiro | Contas a receber da venda, contas a pagar manuais, parcelamento, recebimentos parciais, baixas e estornos |
| Caixa | Abertura e fechamento por operador e movimentações |
| Pós-venda | Trocas e devoluções |
| Consultas | Vendas por período, estoque e títulos em aberto, vencidos ou pagos |

Cor e tamanho são variações do produto. A Nuvemshop é referência de experiência para esse cadastro; seus comportamentos específicos não são automaticamente requisitos do Mirante.

Regras já detalhadas estão em [[07 - Pessoas|Pessoas]], [[08 - Produtos e variações|Produtos e variações]] e [[09 - Estoque|Estoque]]. Estados de venda, cálculo de desconto, parcelamento, caixa e pós-venda ainda precisam de detalhamento, conforme [[13 - Evolução e pendências|Evolução e pendências]].

### Critérios de conclusão da V1

| Cenário | Resultado esperado |
|---|---|
| Preparar a loja | Cadastrar pessoas, produtos e variações e registrar estoque inicial |
| Venda à vista | Finalizar, baixar estoque e registrar recebimento |
| Venda a prazo | Baixar estoque e gerar conta a receber com vencimento |
| Receber posteriormente | Baixar o título sem duplicidade |
| Pagar despesa | Lançar conta a pagar manualmente e registrar pagamento |
| Ajustar estoque | Corrigir a quantidade com motivo e histórico |
| Cancelar venda | Reverter efeitos conforme as regras de estoque e financeiro |
| Repetir finalização | Impedir duplicação da venda, baixa ou cobrança |
| Operar com restrições | Aplicar permissões e isolamento entre empresas e tenants |
| Conferir operação | Consultar vendas, movimentos e títulos consistentes |

Os recursos aprovados de pagamento misto, parcelas, recebimentos parciais, caixa, trocas e devoluções também precisam de critérios específicos antes de sua implementação. A existência desta lista não dispensa o detalhamento desses fluxos.

## Fora da V1

- Fiscal: NF-e, NFC-e, NFS-e, SEFAZ, contingência e regras tributárias completas.
- PDV offline e sincronização.
- Compras e pedidos a fornecedores.
- Integrações bancárias, de pagamento e com marketplaces; conciliação automática.
- Comissões, promoções complexas e múltiplas tabelas de preço.
- Lotes, séries, kits, composição, custo médio, valorização do estoque e margem.
- Relatórios gerenciais avançados.
- Portal comercial completo do revendedor, contratação autônoma de módulos e domínio próprio.
- Verticais como restaurante, oficina e pet shop.

As possibilidades de longo prazo estão em [[13 - Evolução e pendências|Evolução e pendências]].

---

[[00 - Início|← Anterior]] · [[02 - Arquitetura e stack|Próxima →]]
