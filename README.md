# Mirante ERP — Documentação geral

Este vault reúne o **Contexto Mestre do Projeto**, organizado por assunto para leitura e manutenção no Obsidian.

O conteúdo das 26 seções originais foi preservado nas notas abaixo. Os títulos de agrupamento, este índice e os links de navegação são elementos editoriais; não acrescentam decisões arquiteturais. As recomendações da análise posterior não foram incorporadas.

## Navegação

- [[01 - Visão e princípios]] — Objetivos, princípios e expectativas para a IA. Seções originais: 1, 2, 24.
- [[02 - Stack e arquitetura]] — Stack aprovada, monólito modular e fronteiras entre módulos. Seções originais: 3, 4, 5.
- [[03 - White label e multi-tenancy]] — Revendedores, tenants, empresas e vínculo dos usuários. Seções originais: 6, 7, 8.
- [[04 - Autenticação e permissões]] — Perfis, sobrescritas por empresa e autenticação. Seções originais: 9, 10.
- [[05 - Identificadores e API]] — UUID v7, códigos amigáveis, REST e idempotência. Seções originais: 11, 14.
- [[06 - Segurança e auditoria]] — Rastreabilidade de negócio e diretrizes de segurança. Seções originais: 12, 17.
- [[07 - Filas e integrações]] — Uso futuro de Redis e BullMQ e padrões de integração. Seções originais: 13, 16.
- [[08 - PDV offline]] — Escopo futuro, sincronização e limitações do modo offline. Seções originais: 15.
- [[09 - Observabilidade e testes]] — Logs, correlação, saúde, testes e critérios de conclusão. Seções originais: 18, 19.
- [[10 - Desenvolvimento e documentação]] — Repositórios, Git, uso de IA, qualidade e autoridade documental. Seções originais: 20, 21, 22, 23.
- [[11 - Decisões futuras e continuidade]] — Assuntos pendentes e orientação para as próximas etapas. Seções originais: 25, 26.

## Como visualizar no Obsidian

1. Abra o Obsidian.
2. Escolha **Abrir pasta como vault** / **Open folder as vault**.
3. Selecione a pasta que contém este arquivo: **C:\Projetos\WM\mirante-erp-doc**.
4. Abra a nota **README** e navegue pelos links acima.

O vault utiliza apenas Markdown e recursos nativos do Obsidian. Não exige plugins da comunidade. O grafo e os backlinks permitem visualizar as conexões entre as notas.

## Como manter

- Edite o assunto na nota correspondente, evitando criar cópias do mesmo conteúdo.
- Preserve a distinção original entre decisões aprovadas, sugestões, possibilidades futuras e assuntos pendentes.
- Para mudanças macro, siga o processo de discussão, aprovação e registro descrito em [[10 - Desenvolvimento e documentação]].
- Os números dos títulos internos correspondem às seções do documento original; os números dos arquivos indicam apenas a ordem de leitura.
- A pasta .obsidian contém apenas configurações básicas de navegação e edição.

## Por onde começar

Leia [[01 - Visão e princípios]], depois [[02 - Stack e arquitetura]] e [[03 - White label e multi-tenancy]].

As regras de trabalho estão em [[10 - Desenvolvimento e documentação]]. Os assuntos ainda não detalhados estão em [[11 - Decisões futuras e continuidade]].
