# Pessoas

[[00 - Início|Início]] · [[06 - Domínios e propriedade dos dados|Domínios e propriedade dos dados]] · [[04 - Tenants, empresas e acesso|Tenants, empresas e acesso]]

## Responsabilidade

Manter cadastros de pessoas por empresa. Uma pessoa pode acumular os papéis de cliente, fornecedor, transportador e funcionário, sem duplicar o cadastro dentro da empresa para cada papel.

Usuários e pessoas são cadastros separados, sem vínculo nesta etapa. Cadastrar, copiar ou inativar um funcionário não cria, concede ou bloqueia acesso ao sistema. E-mail de contato não altera e-mail de login.

## Campos e regras

| Campo | Regra da V1 |
|---|---|
| Tipo | Pessoa física ou jurídica |
| Nome ou razão social | Obrigatório |
| Nome fantasia | Opcional para pessoa jurídica |
| CPF ou CNPJ | Opcional; validar quando informado |
| Papéis | Cliente, fornecedor, transportador e funcionário; podem ser acumulados |
| Telefone, e-mail e endereço | Opcionais |
| Situação | Ativo ou inativo |

O papel funcionário não inclui folha de pagamento ou rotinas de RH na V1.

## Cadastro em outras empresas

O cadastro pertence à empresa atual. Depois de salvar, se o operador tiver permissão de cadastro em outras empresas do mesmo tenant, o sistema oferece a ação de cadastrar também nelas.

- O operador seleciona explicitamente as empresas; nenhuma vem marcada automaticamente.
- O backend valida a permissão nas empresas de destino.
- O sistema verifica duplicidades e registra a ação na auditoria.
- Cada destino recebe um cadastro independente.
- Alterações posteriores de telefone, endereço ou outros dados não são propagadas automaticamente.
- Dados específicos e papel de funcionário não são copiados para outras empresas.

Permissão de acesso a várias empresas não mistura automaticamente seus cadastros. Cuidados de proteção de dados estão em [[05 - Autenticação e segurança|Autenticação e segurança]].

## Duplicidade

CPF/CNPJ informado não pode se repetir na mesma empresa. Pode existir em empresas diferentes.

Nome igual gera aviso, sem bloqueio. Se o documento já existir em uma empresa de destino, o sistema informa o cadastro encontrado e não o sobrescreve automaticamente.

## Inativação e histórico

Cadastro nunca utilizado pode ser excluído mediante permissão. Cadastro já utilizado deve ser inativado, preservando relacionamentos e histórico.

Pessoa inativa não pode ser selecionada em novas operações. Títulos e operações existentes podem ser concluídos. Alterações cadastrais relevantes são auditadas.

A venda mantém a referência ao cliente, sem copiar seu nome. A consulta utiliza o nome atual do cadastro.

## Pendências

- Tratamento de resultados parciais ao cadastrar em várias empresas.
- Critérios de comparação de nomes e normalização de documentos.
- Campos adicionais necessários a cada papel e suas permissões específicas.
- Detalhes de retomada ou reaproveitamento de cadastro já existente no destino.

---

[[06 - Domínios e propriedade dos dados|← Anterior]] · [[08 - Produtos e variações|Próxima →]]
