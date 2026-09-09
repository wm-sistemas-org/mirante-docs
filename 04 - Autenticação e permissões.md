# Autenticação e permissões

[[README|Início]] · [[03 - White label e multi-tenancy|Anterior]] · [[05 - Identificadores e API|Próxima]]

> Conteúdo do documento mestre original. Seções: 9, 10. A numeração original foi preservada para rastreabilidade.

---

# 9. Perfis e permissões

O sistema utilizará:

> Perfis de acesso.

Cada perfil terá permissões padrão.

As permissões deverão ser definidas de forma granular por:

* módulo;
* ação.

Exemplo:

```text
estoque.visualizar
estoque.criar
estoque.editar
estoque.excluir
estoque.ajustar
estoque.transferir
```

Um usuário poderá estar associado a um perfil.

Exemplo:

```text
Perfil Operador

Estoque:
✓ visualizar
✗ criar
✗ editar
```

Porém existe uma necessidade importante:

Um mesmo usuário pode ter permissões diferentes dependendo da empresa.

Por isso o sistema utilizará:

> Perfil padrão + sobrescritas por empresa.

Exemplo:

```text
Usuário X
Perfil padrão:
Estoque → somente visualizar

Empresa A:
override → pode cadastrar

Empresa B:
herda perfil

Empresa C:
override → sem acesso
```

Regra de resolução:

```text
Permissão específica do usuário na empresa
             ↓
se não existir
             ↓
Permissão definida pelo perfil
```

Na ausência de sobrescrita, prevalece o perfil.

Quando existir uma configuração específica para determinada empresa, ela prevalece.

A interface deverá deixar claro quando uma permissão é:

* herdada;
* sobrescrita.

---

# 10. Autenticação

A autenticação será baseada em:

* e-mail;
* senha;
* JWT de curta duração;
* refresh token.

Fluxo:

```text
Login
  ↓
Validação do usuário
  ↓
Identificação automática do tenant
  ↓
Carregamento das empresas permitidas
  ↓
Usuário seleciona empresa
  ↓
Backend valida
  ↓
Contexto autenticado
  ↓
Permissões
```

Refresh tokens deverão ser:

* seguros;
* revogáveis;
* invalidados no logout;
* invalidados quando necessário.

Recuperação de senha será feita por mecanismo seguro através de e-mail.

## Futuro

A arquitetura deverá permitir futuramente:

* MFA;
* SSO.

Esses recursos não precisam estar presentes na primeira versão.

---

---

[[README|Início]] · [[03 - White label e multi-tenancy|Anterior]] · [[05 - Identificadores e API|Próxima]]
