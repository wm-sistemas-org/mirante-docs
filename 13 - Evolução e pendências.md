# Evolução e pendências

[[00 - Início|Início]] · [[01 - Visão e escopo|Visão e escopo]] · [[12 - Desenvolvimento e documentação|Desenvolvimento e documentação]]

## Direção de evolução

A fundação V0 e o núcleo operacional V1 estão delimitados em [[01 - Visão e escopo|Visão e escopo]]. As etapas posteriores podem incluir maturação de compras, comercial, estoque, financeiro e relatórios; fiscal, PDV e integrações; depois verticais.

A ordem exata, datas e números de versões posteriores não estão fechados. Não transformar essa direção em compromisso de cronograma.

Possibilidades de longo prazo incluem marketplaces, gateways, Open Finance, BI, bancos, WhatsApp, restaurante, oficina, pet shop e outras verticais. Contratação autônoma de módulos, domínio próprio e compartilhamento seletivo de produtos também são futuros.

## Próximas regras de negócio a definir

O escopo de vendas, financeiro e caixa já foi aprovado. Seus comportamentos detalhados ainda não foram fechados.

| Assunto | Definições pendentes |
|---|---|
| Vendas | Pedido versus venda, estados, obrigatoriedade de cliente, descontos, acréscimos, edição após finalização e número amigável |
| Pagamento misto | Distribuição entre formas, validação do total, troco e efeitos de cancelamento |
| Financeiro | Parcelas, vencimentos, recebimento parcial, formas de pagamento, contas financeiras, baixas e estornos |
| Caixa | Abertura e fechamento por operador, valores iniciais, movimentações, conferência e diferenças |
| Trocas e devoluções | Quantidades parciais, vínculo com a venda, diferença de preço, restituição/crédito e venda já recebida |

As garantias de estoque para esses fluxos estão aprovadas em [[09 - Estoque|Estoque]]. Detalhar os efeitos financeiros não pode contradizê-las.

## Pendências por assunto

- [[03 - Plataforma e revendedores|Plataforma e revendedores]]: marca no login, reativação, módulos desabilitados, transição de atendimento e detalhes comerciais.
- [[04 - Tenants, empresas e acesso|Tenants, empresas e acesso]]: catálogo de permissões, delegação e operações em andamento.
- [[05 - Autenticação e segurança|Autenticação e segurança]]: tokens, e-mail, secrets, rate limiting, proteção de dados e retenção.
- [[06 - Domínios e propriedade dos dados|Domínios e propriedade dos dados]]: contratos, eventos, entidades e coordenação transacional.
- [[07 - Pessoas|Pessoas]]: cópia em múltiplas empresas, duplicidade e campos específicos dos papéis.
- [[08 - Produtos e variações|Produtos e variações]]: atributos, códigos de barras, geração de SKU, troca de modo e precisão.
- [[09 - Estoque|Estoque]]: contagem concorrente, mudança de controle e devoluções sem retorno ao saldo disponível.
- [[10 - API e integrações|API e integrações]]: formato da API, mecanismos de idempotência, retries e credenciais.
- [[11 - Auditoria, observabilidade e testes|Auditoria, observabilidade e testes]]: retenção, acesso e campos da auditoria, ferramentas de monitoramento.

## Infraestrutura e interface

Antes do piloto em produção, definir ambientes, cloud, CI/CD, migrations, procedimento de implantação, storage para logos/arquivos, backups, teste de restauração, monitoramento mínimo e suporte.

Design system, telas, navegação e detalhes de experiência permanecem pendentes. O frontend deve mostrar marca, empresa ativa, erros e permissões com clareza.

Schema Prisma, tabelas, relacionamentos e estrutura interna pertencem à documentação técnica e serão definidos com base nos domínios aprovados.

## PDV offline futuro

O ERP web é prioridade. O offline será voltado a operações essenciais de PDV, sem tornar todo o ERP offline.

Possíveis operações: vendas, pessoas, abertura/movimentação/fechamento de caixa, consulta de produtos e preços.

A direção conceitual é armazenamento local e fila de sincronização, enviados à API quando a conexão retorna. O backend permanece fonte oficial.

O offline precisará de UUID v7 local, sincronização, idempotência, retries, fila local, versões de registros e resolução de conflitos. As regras de saldo negativo e concorrência do modo online não definem automaticamente a política de reconciliação offline.

Tecnologia de PDV permanece aberta; C# e Flutter são possibilidades, não decisões. A implementação atual deve evitar impedimentos estruturais, sem implementar a sincronização antecipadamente.

## Critério para novas funcionalidades

Avaliar o problema, necessidade no fluxo atual, caráter comum ou especializado, dependências, clareza das regras, impacto transversal e possibilidade de adiar.

Priorizar fluxos completos úteis ao piloto. Infraestrutura distribuída, Kubernetes, sharding, réplicas de leitura, service mesh e clusters adicionais não são necessidades aprovadas da primeira etapa.

---

[[12 - Desenvolvimento e documentação|← Anterior]]
