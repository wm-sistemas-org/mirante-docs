# Segurança e auditoria

[[README|Início]] · [[05 - Identificadores e API|Anterior]] · [[07 - Filas e integrações|Próxima]]

> Conteúdo do documento mestre original. Seções: 12, 17. A numeração original foi preservada para rastreabilidade.

---

# 12. Auditoria

O ERP possuirá auditoria nativa desde o início.

Auditoria é diferente de log técnico.

## Auditoria de negócio

Deverá registrar, quando aplicável:

* usuário;
* tenant;
* empresa;
* data/hora;
* módulo;
* ação;
* entidade;
* registro afetado;
* valores anteriores;
* valores posteriores;
* origem da operação.

Exemplos de ações importantes:

* alteração de preço;
* ajuste de estoque;
* baixa financeira;
* cancelamento;
* exclusão;
* alteração fiscal;
* alteração de permissões;
* alteração de configuração crítica;
* estorno.

Operações críticas deverão obrigatoriamente possuir auditoria.

Principalmente:

* financeiro;
* fiscal;
* estoque;
* permissões;
* cancelamentos;
* exclusões;
* configurações sensíveis.

A auditoria não poderá ser alterada por usuários comuns.

## O que NÃO será auditado inicialmente

Não será registrado:

* onde o usuário clicou;
* abertura de menus;
* abertura de telas;
* paginações;
* navegação;
* ações puramente de interface.

Caso futuramente exista interesse em medir comportamento de uso, isso será tratado como:

> telemetria/analytics.

Não como auditoria.

---

# 17. Segurança

Segurança deverá existir em múltiplas camadas.

## Isolamento multi-tenant

Um tenant nunca poderá acessar dados de outro tenant.

O backend sempre validará:

```text
Usuário
  ↓
Tenant
  ↓
Empresa
  ↓
Permissões
  ↓
Operação
```

Segurança não poderá depender apenas do frontend.

Esconder um botão no frontend não substitui autorização no backend.

## Senhas

Senhas:

* nunca serão armazenadas em texto puro;
* deverão utilizar hash seguro;
* Argon2id é candidato principal;
* nunca serão registradas em logs.

## Tokens

Refresh tokens deverão:

* ser protegidos;
* ser revogáveis;
* ser invalidados quando necessário.

## Secrets

Secrets nunca poderão ser commitados no Git.

Exemplos:

* senha do PostgreSQL;
* JWT secret;
* API keys;
* tokens;
* certificados;
* credenciais Open Finance.

## Comunicação

Todo tráfego de produção deverá utilizar:

> HTTPS/TLS.

## LGPD

A arquitetura deverá considerar LGPD desde o início.

O ERP armazenará dados pessoais e empresariais sensíveis.

Deverá existir suporte futuro para:

* políticas de retenção;
* anonimização quando legalmente aplicável;
* exportação;
* controle de acesso;
* proteção de backups.

Requisitos fiscais e legais podem impedir exclusão imediata de determinados dados.

## Rate limiting

Endpoints sensíveis deverão suportar rate limiting.

Principalmente:

* login;
* recuperação de senha;
* endpoints públicos;
* webhooks;
* APIs externas.

## OWASP

O sistema deverá seguir boas práticas de segurança para aplicações web e APIs.

Incluindo proteção contra:

* SQL Injection;
* XSS;
* CSRF quando aplicável;
* SSRF;
* brute force;
* upload malicioso;
* path traversal;
* mass assignment;
* broken authorization;
* exposição indevida de dados.

## Logs

Logs nunca deverão expor:

* senhas;
* tokens;
* credenciais;
* certificados;
* dados bancários completos;
* informações sensíveis desnecessárias.

## Princípio do menor privilégio

Usuários, serviços e integrações deverão acessar apenas aquilo que realmente necessitam.

---

---

[[README|Início]] · [[05 - Identificadores e API|Anterior]] · [[07 - Filas e integrações|Próxima]]
