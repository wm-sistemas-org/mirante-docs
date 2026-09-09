# PDV offline

[[README|Início]] · [[07 - Filas e integrações|Anterior]] · [[09 - Observabilidade e testes|Próxima]]

> Conteúdo do documento mestre original. Seções: 15. A numeração original foi preservada para rastreabilidade.

---

# 15. Offline futuro

O ERP web será prioridade.

O modo offline será implementado futuramente.

A intenção não é tornar o ERP inteiro offline.

O offline será voltado principalmente à operação de PDV.

Possíveis operações offline:

* vendas;
* cadastro de pessoas;
* abertura de caixa;
* movimentações de caixa;
* fechamento de caixa;
* consulta de produtos;
* consulta de preços;
* operações essenciais do PDV.

Arquitetura conceitual:

```text
PDV
 ├── armazenamento local
 ├── vendas
 ├── pessoas
 ├── caixa
 └── fila local de sincronização
          ↓
     conexão retorna
          ↓
       API REST
          ↓
       Backend
          ↓
     PostgreSQL
```

O backend continuará sendo a fonte oficial dos dados.

O modo offline deverá suportar:

* UUID v7 local;
* sincronização;
* idempotência;
* retries;
* fila local;
* controle de versão dos registros;
* tratamento de conflitos.

O desenvolvimento inicial do ERP não precisa implementar essa funcionalidade.

Apenas deve evitar decisões arquiteturais que impeçam sua implementação futura.

A tecnologia do PDV offline, possivelmente C# ou Flutter, ainda será decidida posteriormente.

---

---

[[README|Início]] · [[07 - Filas e integrações|Anterior]] · [[09 - Observabilidade e testes|Próxima]]
