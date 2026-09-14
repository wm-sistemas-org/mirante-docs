# Mirante ERP — Documentação geral

Este vault contém as regras vigentes, o escopo aprovado e a direção arquitetural do Mirante ERP. A documentação é organizada por assunto; pendências e possibilidades futuras são identificadas explicitamente.

## Produto e plataforma

- [[01 - Visão e escopo|Visão e escopo]] — Público do piloto, V0, V1, exclusões e critérios de conclusão.
- [[02 - Arquitetura e stack|Arquitetura e stack]] — Tecnologias, monólito modular e regras de fronteira.
- [[03 - Plataforma e revendedores|Plataforma e revendedores]] — Painéis, clientes diretos, white label, módulos e suspensões.
- [[04 - Tenants, empresas e acesso|Tenants, empresas e acesso]] — Isolamento, tipos de conta, contexto por aba e permissões.
- [[05 - Autenticação e segurança|Autenticação e segurança]] — Login, sessões, proteção da aplicação e dados pessoais.

## Domínios

- [[06 - Domínios e propriedade dos dados|Domínios e propriedade dos dados]] — Responsabilidades e escopos de dados.
- [[07 - Pessoas|Pessoas]] — Papéis, campos, duplicidade e cadastro independente em outras empresas.
- [[08 - Produtos e variações|Produtos e variações]] — Catálogos, atributos, códigos, preços e inativação.
- [[09 - Estoque|Estoque]] — Saldos, movimentações, baixas e reversões.

Vendas, Financeiro e Caixa têm escopo aprovado em [[01 - Visão e escopo|Visão e escopo]]. Ganharão notas de domínio conforme suas regras forem detalhadas.

## Engenharia e continuidade

- [[10 - API e integrações|API e integrações]] — REST, IDs, idempotência, adapters e filas futuras.
- [[11 - Auditoria, observabilidade e testes|Auditoria, observabilidade e testes]] — Rastreabilidade, diagnóstico e qualidade.
- [[12 - Desenvolvimento e documentação|Desenvolvimento e documentação]] — Git, revisão, IA e manutenção documental.
- [[13 - Evolução e pendências|Evolução e pendências]] — Próximas definições e funcionalidades futuras.

## Como utilizar

No Obsidian, abra a pasta C:\Projetos\WM\mirante-erp-doc como vault e comece por esta nota. Os links, backlinks e o grafo são recursos nativos; a documentação não exige plugins da comunidade.

Comece por [[01 - Visão e escopo|Visão e escopo]], [[02 - Arquitetura e stack|Arquitetura e stack]] e [[06 - Domínios e propriedade dos dados|Domínios e propriedade dos dados]]. Antes de implementar, consulte a nota responsável e suas pendências.

O histórico fica no Git. Regras de manutenção e autoridade documental estão em [[12 - Desenvolvimento e documentação|Desenvolvimento e documentação]].

Os números dos arquivos indicam somente a ordem de leitura. As regras continuam organizadas por assunto.

---

[[01 - Visão e escopo|Próxima →]]
