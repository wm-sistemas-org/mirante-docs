# Autenticação e segurança

[[00 - Início|Início]] · [[04 - Tenants, empresas e acesso|Tenants, empresas e acesso]] · [[11 - Auditoria, observabilidade e testes|Auditoria, observabilidade e testes]]

## Autenticação

O login utiliza e-mail único na plataforma, senha, JWT de curta duração e refresh token. A V0 inclui login funcional, logout, revogação e recuperação de senha por e-mail.

Para contas operacionais, o backend identifica o tenant a partir da conta autenticada, lista empresas permitidas e valida a seleção. Administradores seguem o vínculo de seu tipo de conta.

Refresh tokens devem ser protegidos, revogáveis e invalidados no logout e quando necessário. Usuário suspenso tem o acesso bloqueado e as sessões revogadas.

Senhas nunca são armazenadas em texto puro nem registradas em logs. Deve ser utilizado hash seguro; Argon2id permanece o candidato principal. MFA e SSO são possibilidades futuras.

## Autorização e isolamento

A autorização é aplicada no backend. Esconder um botão não substitui a validação da operação. Contextos de tenant e empresa, acesso ao módulo e permissões devem ser respeitados também fora das telas, em rotinas e integrações.

As regras de contas, empresas e sobrescritas estão em [[04 - Tenants, empresas e acesso|Tenants, empresas e acesso]].

## Proteção da aplicação

- Tráfego de produção por HTTPS/TLS.
- Secrets, tokens, certificados, senhas e credenciais nunca são commitados nem expostos ao frontend.
- Princípio do menor privilégio para usuários, serviços e integrações.
- Rate limiting em login, recuperação de senha e outros endpoints públicos ou sensíveis, incluindo webhooks quando existirem.
- Proteção contra SQL injection, XSS, CSRF quando aplicável, SSRF, brute force, upload malicioso, path traversal, mass assignment, falhas de autorização e exposição de dados.
- Logs não expõem senhas, tokens, credenciais, certificados, dados bancários completos ou informações sensíveis desnecessárias.

## LGPD e dados pessoais

A arquitetura deve considerar proteção de dados, controle de acesso, políticas de retenção, exportação, anonimização quando aplicável e proteção de backups. Obrigações legais e fiscais podem limitar a exclusão de dados.

O cadastro em outras empresas segue [[07 - Pessoas|Pessoas]]. A confirmação do operador registra a ação de cadastro; não deve ser apresentada como consentimento do titular ou garantia automática de conformidade.

Finalidades, responsabilidades de tratamento e políticas aplicáveis ao piloto permanecem assuntos a detalhar.

## Pendências antes da implementação ou produção

- Armazenamento de tokens no cliente e servidor, rotação, validade e recuperação de sessões.
- Parâmetros do hash de senha e políticas de recuperação.
- Serviço de e-mail, conteúdo e contexto de marca das mensagens.
- Regras e infraestrutura de rate limiting.
- Gestão de secrets, retenção e proteção de dados e backups.

---

[[04 - Tenants, empresas e acesso|← Anterior]] · [[06 - Domínios e propriedade dos dados|Próxima →]]
