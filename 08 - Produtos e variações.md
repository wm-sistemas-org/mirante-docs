# Produtos e variações

[[00 - Início|Início]] · [[06 - Domínios e propriedade dos dados|Domínios e propriedade dos dados]] · [[09 - Estoque|Estoque]]

## Responsabilidade

Manter catálogo de produtos simples ou com variações, categorias, unidades e identificação dos itens vendáveis. A experiência de variações terá a Nuvemshop como referência; detalhes específicos ainda precisam de definição.

## Modos de catálogo

Na etapa inicial, o tenant possui um de dois modos:

| Modo | Comportamento |
|---|---|
| Compartilhado | Empresas utilizam o mesmo catálogo de produtos e variações |
| Separado | Cada empresa mantém seu catálogo independente |

No modo compartilhado, nome, descrição, códigos, atributos, categoria e unidade pertencem ao catálogo comum. Preços, habilitação comercial e estoque permanecem por empresa nos dois modos.

Cada empresa pode habilitar ou desabilitar a comercialização de um produto. Um produto novo não precisa ser disponibilizado automaticamente em todas as empresas.

A seleção de produtos individuais para compartilhar/importar em uma empresa é futura. Copiar um cadastro independente e vincular um produto comum são comportamentos distintos ainda a detalhar. A troca de modo após existirem cadastros e operações também está pendente.

## Produto e variação

| Produto | Variação ou item vendável |
|---|---|
| Nome obrigatório | Combinação de atributos, como cor e tamanho |
| Descrição complementar opcional | SKU próprio |
| Categoria opcional | Código de barras opcional |
| Unidade obrigatória | Preço por empresa |
| Situação | Situação e saldo por empresa |

Produtos sem variações são cadastrados normalmente. Quando existem variações, a venda seleciona uma combinação específica. Camiseta preta P e preta M possuem identificação e saldo próprios.

## Identificadores

- UUID v7: identificador técnico gerado pelo sistema.
- Código interno/SKU: código visível, gerado automaticamente se não informado; cada variação tem seu próprio código.
- Código de barras: opcional, usado para leitura e pesquisa.

O SKU é único no escopo do catálogo: tenant no compartilhado, empresa no separado. Não haverá um terceiro código amigável redundante para a mesma finalidade.

## Categorias e unidades

Na V1, cada produto tem no máximo uma categoria, sem hierarquia de subcategorias. Categorias e unidades acompanham o escopo compartilhado ou separado do catálogo.

A unidade indica se aceita quantidade inteira ou fracionada. Camiseta em UN aceita unidades inteiras; produto em metro pode aceitar frações.

Conversão automática entre caixa, pacote e unidade fica fora desta etapa.

## Preço e operação por empresa

Cada variação pode ter preço por empresa. A interface pode facilitar preenchimento conjunto, sem eliminar a separação dos preços.

A configuração de controle de estoque e seus efeitos estão em [[09 - Estoque|Estoque]].

## Inativação e histórico de vendas

Cadastro nunca utilizado pode ser excluído mediante permissão. Produto ou variação já utilizado deve ser inativado.

Itens inativos ficam indisponíveis para novas vendas, mas continuam no histórico e nas devoluções. Alterações relevantes são auditadas.

A venda referencia o produto/item vendável e consulta seu nome atual no cadastro. Não salva uma descrição própria: alterações do nome aparecem também em vendas antigas. Essa regra de descrição não define os demais valores históricos da venda, que ainda serão detalhados.

## Limites e pendências

Lotes, séries, kits, composição e múltiplas tabelas de preço não fazem parte da V1.

Permanecem pendentes: limites e edição dos atributos/combinações, unicidade e validação do código de barras, algoritmo de geração de SKU, precisão de quantidades e valores, e comportamento de cadastro novo em cada modo de catálogo.

---

[[07 - Pessoas|← Anterior]] · [[09 - Estoque|Próxima →]]
