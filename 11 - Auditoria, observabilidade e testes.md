# Auditoria, observabilidade e testes

[[00 - Início|Início]] · [[05 - Autenticação e segurança|Autenticação e segurança]] · [[12 - Desenvolvimento e documentação|Desenvolvimento e documentação]]

## Auditoria de negócio

Auditoria é nativa desde a V0 e distinta de log técnico. Registra, quando aplicável:

- Ator/usuário, tenant e empresa.
- Data/hora, módulo, ação e origem.
- Entidade e registro afetado.
- Valores anteriores e posteriores.

Na fundação, devem ser auditáveis criação e alteração de usuários, perfis, permissões, acessos às empresas, configurações críticas e ações administrativas relevantes.

Operações críticas de estoque, financeiro, fiscal futuro, preços, cancelamentos, estornos e exclusões devem possuir auditoria. Cadastro de pessoas em outras empresas também deve ser registrado.

Usuários comuns não podem alterar a auditoria. Cliques, abertura de telas, menus, paginação e navegação não são auditados inicialmente. Eventual analytics será tratado separadamente.

Campos permitidos, retenção, consulta e atomicidade do registro de auditoria precisam de detalhamento; as restrições de dados sensíveis seguem [[05 - Autenticação e segurança|Autenticação e segurança]].

## Logs e correlação

Logs técnicos devem ser estruturados, com nível, mensagem, módulo, timestamp, request ID e contexto de tenant, empresa e provedor quando aplicável.

Cada requisição possui identificador para correlacionar frontend, backend, módulo, fila e integração. Devem existir logs de inicialização, falhas importantes e tratamento centralizado de erros.

Erros seguem padrão; VALIDATION_ERROR, ACCESS_DENIED e INTEGRATION_TIMEOUT são exemplos. Stack traces não são enviados ao usuário, que pode receber um código de referência para suporte. O catálogo definitivo está pendente em [[10 - API e integrações|API e integrações]].

## Saúde e métricas

A V0 inclui health checks dos componentes efetivamente utilizados, inicialmente API e PostgreSQL.

Métricas futuras podem incluir latência, erros, CPU, memória, conexões, filas, jobs e falhas externas. A escolha de fornecedor de monitoramento permanece aberta; Sentry, Grafana, OpenTelemetry e Datadog não estão aprovados como dependências obrigatórias.

## Estratégia de testes

Testes automatizados são obrigatórios conforme necessidade: unitários, integração, E2E e contratos.

Áreas críticas incluem isolamento, autenticação, autorização, permissões, estoque, financeiro, idempotência, cancelamentos e integrações/fiscal quando implementados.

Devem existir testes de que um usuário do tenant A não acessa dados do B e de que as empresas do mesmo tenant respeitam seus escopos e permissões. Mudanças de permissões, refresh tokens e operações da fundação também precisam de cobertura.

Correções de bugs devem incluir regressão reproduzindo o problema sempre que possível. Cobertura percentual é indicador, sem substituir testes de regras relevantes.

## Critérios de conclusão de uma tarefa

Quando aplicável:

- Implementação pronta e dentro do escopo.
- Lint, build e testes existentes passando.
- Novos testes necessários incluídos.
- Permissões, auditoria e regras arquiteturais respeitadas.
- Documentação atualizada.
- Pull request revisado por humano.

Os cenários de conclusão da V0 e V1 estão em [[01 - Visão e escopo|Visão e escopo]].

---

[[10 - API e integrações|← Anterior]] · [[12 - Desenvolvimento e documentação|Próxima →]]
