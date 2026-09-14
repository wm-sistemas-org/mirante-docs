# Plataforma e revendedores

[[00 - Início|Início]] · [[04 - Tenants, empresas e acesso|Tenants, empresas e acesso]] · [[05 - Autenticação e segurança|Autenticação e segurança]]

## Responsabilidade

Administrar a plataforma, seus revendedores e clientes diretos, o white label e os módulos disponíveis por empresa.

## Atendimento e hierarquia

A WM administra a plataforma. Um tenant pode ser atendido por um revendedor ou diretamente pela WM, sem revendedor intermediário.

- WM → revendedor → tenant → empresas.
- WM → tenant direto → empresas.

Transferir o atendimento para a WM preserva a identidade do tenant e seus dados. O revendedor não é a chave principal de isolamento.

## Painéis da V0

| Painel | Atribuições |
|---|---|
| WM | Administrar revendedores, tenants diretos ou vinculados, empresas, situações e habilitação de módulos |
| Revendedor | Administrar seus próprios clientes e habilitar módulos permitidos nas empresas desses tenants |

Administradores não recebem acesso automático a vendas, estoque ou financeiro dos clientes. Acesso operacional para suporte não faz parte desta etapa.

O primeiro administrador WM será criado por procedimento inicial controlado. Administradores seguintes serão criados pelo painel.

## Módulos por empresa

A WM ou o revendedor habilita módulos por empresa, dentro de sua área de administração e dos módulos permitidos pela plataforma. Habilitação comercial não substitui autorização do usuário.

A contratação de módulos pela própria empresa é futura.

## Suspensões

| Situação | Efeito aprovado |
|---|---|
| Revendedor suspenso e tenant assumido pela WM | Preservar usuários, empresas, dados e vínculos internos; alterar o responsável pelo atendimento |
| Revendedor suspenso e tenant não assumido | Desativar o acesso ao tenant |
| Tenant ou empresa suspensa individualmente | Permitir somente consulta, respeitando as permissões existentes |
| Usuário suspenso | Bloquear acesso e revogar sessões |

Na suspensão do revendedor, o painel oferece à WM a opção de assumir seus tenants. A regra para tenants não assumidos poderá evoluir comercialmente no futuro.

## White label

White label é nativo e baseado em configuração, sem condições específicas de revendedores espalhadas pelo código.

O domínio principal previsto é miranteerp.com.br, com subdomínios como revendedor.miranteerp.com.br. Na V0, a marca inclui nome, logo, cores principais e identificação/contexto do revendedor.

Favicon, identidade de e-mail e nome em comunicações fazem parte da capacidade prevista de personalização. Domínio próprio/CNAME, construtor de temas e personalização avançada não entram na primeira etapa.

O subdomínio não concede autorização de dados. O comportamento exato ao entrar pelo endereço principal ou pelo endereço de outro revendedor permanece pendente.

## Responsabilidades comerciais e operacionais

A plataforma responde por infraestrutura, segurança, atualizações, versões, banco, backups, limites técnicos, integrações centrais, módulos disponíveis e suporte avançado.

O revendedor responde pela relação comercial, preço ao cliente, marca e suporte de primeiro nível. A plataforma cobra do revendedor, que define o valor ao cliente final. Empresas/CNPJs ativos são a referência prevista de cobrança; preços e critérios comerciais detalhados permanecem pendentes. A cobrança dos clientes atendidos diretamente pela WM também precisa de detalhamento.

## Pendências

- Regras de reativação e consequências de módulos desabilitados em operações existentes.
- Procedimento técnico de criação do primeiro administrador.
- URLs dos painéis e comportamento de marca/redirecionamento no login.
- Procedimento de troca de marca e endereço quando a WM assume um tenant.

---

[[02 - Arquitetura e stack|← Anterior]] · [[04 - Tenants, empresas e acesso|Próxima →]]
