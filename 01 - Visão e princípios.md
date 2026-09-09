# Visão e princípios

[[README|Início]] · [[02 - Stack e arquitetura|Próxima]]

> Conteúdo do documento mestre original. Seções: 1, 2, 24. A numeração original foi preservada para rastreabilidade.

---

## 1. Visão geral do projeto

Estamos iniciando o desenvolvimento de um novo ERP chamado **Mirante ERP**.

O objetivo é construir um ERP web moderno, modular, escalável e preparado para crescer por muitos anos.

Não estamos construindo apenas um sistema comercial simples. A expectativa é que, ao longo do tempo, a plataforma tenha recursos como:

* vendas;
* estoque;
* financeiro;
* fiscal;
* compras;
* integrações com marketplaces;
* gateways de pagamento;
* Open Finance;
* BI;
* integrações bancárias;
* módulos especializados;
* restaurante;
* oficina;
* pet shop;
* PDV offline;
* outras verticais futuras.

O sistema também será **white label**, permitindo que revendedores comercializem o ERP utilizando sua própria marca.

O desenvolvimento será realizado inicialmente por dois desenvolvedores:

* Murilo;
* Felipe.

O projeto será desenvolvido com forte utilização de inteligência artificial, mas a IA deverá trabalhar dentro de regras arquiteturais e de qualidade bem definidas.

Nosso objetivo é conseguir evoluir o sistema rapidamente sem gerar uma base de código desorganizada ou difícil de manter.

A IA deve atuar como ferramenta de desenvolvimento e apoio arquitetural, mas não deve tomar decisões estruturais importantes sem aprovação humana.

---

# 2. Princípios gerais do projeto

O Mirante ERP deve ser construído com os seguintes princípios:

* arquitetura preparada para crescimento;
* código legível para humanos;
* forte separação de responsabilidades;
* modularidade;
* segurança desde o início;
* multi-tenancy nativo;
* white label nativo;
* documentação como parte do desenvolvimento;
* testes automatizados;
* integração com IA;
* baixa complexidade operacional inicialmente;
* evitar overengineering;
* não adicionar tecnologias ou abstrações sem necessidade real;
* permitir evolução gradual da arquitetura.

Uma regra importante do projeto será:

> Complexidade arquitetural ou de infraestrutura só deve ser introduzida quando existir uma necessidade concreta que a justifique.

---

# 24. Expectativa em relação à IA que receber este documento

Ao receber este documento, a IA deverá assumir que as decisões aqui marcadas como definidas já foram discutidas e aprovadas.

Ela não deverá reinterpretá-las ou substituí-las silenciosamente.

Esperamos que a IA:

1. entenda o contexto completo do Mirante ERP;
2. respeite as decisões já tomadas;
3. questione decisões apenas quando houver motivo técnico relevante;
4. explique riscos antes de sugerir alterações;
5. não introduza tecnologias desnecessárias;
6. não faça overengineering;
7. produza código organizado e legível;
8. mantenha documentação e código alinhados;
9. respeite multi-tenancy e segurança em todas as implementações;
10. priorize manutenção de longo prazo;
11. trabalhe dentro do escopo solicitado;
12. proponha ADR quando uma nova decisão arquitetural for necessária;
13. não trate sugestões como decisões aprovadas;
14. diferencie claramente:

* decisão fechada;
* recomendação;
* possibilidade futura;
* detalhe ainda não definido.

A IA também deve considerar que este ERP poderá crescer bastante ao longo dos próximos anos.

Por isso deve equilibrar dois objetivos:

> não criar arquitetura descartável;

e ao mesmo tempo:

> não construir complexidade de uma empresa gigante antes que essa complexidade seja necessária.

---

---

[[README|Início]] · [[02 - Stack e arquitetura|Próxima]]
