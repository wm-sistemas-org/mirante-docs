# Estoque

[[00 - Início|Início]] · [[08 - Produtos e variações|Produtos e variações]] · [[06 - Domínios e propriedade dos dados|Domínios e propriedade dos dados]]

## Responsabilidade e local

Estoque controla saldos e movimentações. A V1 tem um único local de estoque por empresa. Múltiplos depósitos e transferências entre locais ficam para depois.

Mesmo em catálogo compartilhado, cada empresa possui seu saldo. Produtos com variações têm saldo por combinação.

## Saldo negativo e controle

Saídas que deixem estoque negativo são bloqueadas. Divergência física deve ser corrigida por usuário autorizado, mediante ajuste justificado, antes da venda.

A configuração por produto e empresa possui duas opções:

| Opção | Comportamento |
|---|---|
| Controla estoque | Movimenta saldo e verifica disponibilidade na venda |
| Não controla estoque | Permite venda sem verificar saldo e sem movimentação de estoque |

A configuração vale para todas as variações do produto naquela empresa. Sua alteração depois de movimentações exige regra específica ainda pendente.

## Movimentações

O saldo é consequência das movimentações. Não há alteração direta e silenciosa.

| Operação | Registro |
|---|---|
| Saldo inicial | Entrada identificada como implantação |
| Entrada manual | Item, quantidade e motivo |
| Saída manual | Item, quantidade e motivo, como perda ou avaria |
| Ajuste por contagem | Quantidade contada e movimento da diferença |

Exemplo: saldo atual 10 e contagem 8 geram ajuste de −2, preservando o histórico.

Entradas manuais não geram contas a pagar automaticamente. O financeiro é lançado separadamente nesta etapa.

## Baixa na venda

A baixa ocorre somente na finalização da venda. Rascunho não movimenta nem reserva estoque.

A disponibilidade exibida durante o preenchimento é informativa. O backend verifica novamente na finalização. Duas vendas em rascunho podem disputar o saldo, mas não podem consumir a mesma última unidade.

## Reversões e pós-venda

Movimentações originais são preservadas; correções geram movimentos de reversão.

| Operação | Efeito |
|---|---|
| Cancelamento de venda | Repor o estoque baixado quando a mercadoria não saiu ou foi efetivamente devolvida |
| Devolução | Repor somente quantidades recebidas e aptas a voltar ao estoque disponível |
| Troca | Registrar devolução do item recebido e saída do novo item |
| Correção manual | Estornar o movimento incorreto e registrar outro, com permissão e justificativa |

Cancelar um recebimento financeiro, por si só, não movimenta estoque. Uma reversão que implique saída também deve respeitar a regra de saldo negativo.

## Integridade e auditoria

- Repetir a finalização não pode gerar nova baixa.
- Falha de finalização não pode deixar uma baixa isolada de uma venda não concluída.
- Vendas simultâneas não podem consumir o mesmo saldo disponível.
- Os registros identificam empresa, produto/variação, quantidade, origem, usuário, data e motivo quando aplicável.
- Operações críticas são auditadas conforme [[11 - Auditoria, observabilidade e testes|Auditoria, observabilidade e testes]].

O mecanismo de transação e proteção de concorrência será detalhado na implementação, sem alterar essas garantias.

## Fora da V1

Custo médio, valorização do estoque e cálculo de margem. O controle inicial é de quantidades.

## Pendências

- Precisão de quantidades e tratamento de contagem diante de movimentações simultâneas.
- Regras para alterar a configuração de controle após movimentações.
- Detalhes de devoluções não aptas a retornar ao estoque disponível.
- Contratos e transações com Vendas e Financeiro.

---

[[08 - Produtos e variações|← Anterior]] · [[10 - API e integrações|Próxima →]]
