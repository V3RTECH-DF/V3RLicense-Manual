---
title: Política de Privacidade
parent: Legal
nav_order: 1
---

# Política de Privacidade

**V3RLicense — Servidor de Licenças dos Plugins WordPress da V3RTECH e da RIT**

Versão 0.1 (minuta) — Agosto de 2026

---

{: .warning }
> **Minuta pendente de revisão do dono do produto.**
>
> Este documento foi produzido por adaptação da política do V3REvent e por
> levantamento direto do schema de dados do V3RLicense — não foi redigido
> nem revisado por quem responde juridicamente pelo produto. As bases legais
> propostas aqui são **sugestão fundamentada**, não decisão. Não trate como
> vigente até a revisão acontecer; o relatório da sessão que produziu esta
> minuta lista as perguntas em aberto (prazo de retenção e contato de DPO
> confirmado, entre outras).

---

## Quem é o controlador

{: .important }
> Diferente dos plugins que licencia, o **V3RLicense não é auto-hospedado
> pelo cliente**: ele roda em infraestrutura da própria V3RTECH
> (`v3rtech.com.br`) e é operado pela equipe V3RTECH/RIT. Por isso, aqui a
> **V3RTECH é a controladora** dos dados pessoais tratados por este sistema
> — não há um "controlador terceiro" para quem repassar essa
> responsabilidade, como acontece na política de cada plugin.

## O que este sistema trata, e por quê

| Dado | Onde fica | Origem | Finalidade proposta | Base legal proposta |
|---|---|---|---|---|
| Nome e e-mail de contato da organização cliente | Cadastro de clientes | Digitado por um operador ao emitir uma licença (ou editado depois) | Identificar a quem uma licença pertence, para emissão, renovação, revogação e comunicação sobre o serviço | **Execução de contrato ou procedimentos preliminares** (Art. 7º, V, LGPD) — a licença, paga ou concedida por isenção, é uma relação entre a V3RTECH/RIT e a organização cliente, e o contato é indispensável para administrá-la |
| Anotação livre em uma licença | Cadastro de licenças | Texto digitado pelo operador na emissão | Registro interno do motivo/contexto de uma licença (ex.: número de pedido, confirmação de filiação) | Mesma base do item acima — mas ver alerta abaixo |
| Domínio, versão do plugin/PHP/WordPress e datas de uso | Registro de ativações | Enviado automaticamente pelo plugin instalado no site do cliente, ao ativar/consultar a licença | Controlar quantos sites usam uma licença (cota de ativação) e apurar problema técnico | Ver discussão abaixo — depende de quem é o titular |

{: .warning }
> **A anotação livre da licença pode virar dado pessoal por descuido.** O
> campo existe para contexto operacional ("pedido #4821, boleto pago em
> 20/08"), mas nada impede alguém de colar ali um nome completo, um CPF ou
> outro dado sensível que não precisaria estar registrado. **Recomendação:**
> use a anotação só para o mínimo necessário à gestão da licença — número de
> pedido, data, motivo da origem — e nunca para dado de identificação
> pessoal que já não esteja no cadastro de cliente.

### O registro de ativação é dado pessoal?

Normalmente, não diretamente: um domínio de site pertence a uma organização, não a uma pessoa física identificável por ele. **Isso muda quando o cliente é uma pessoa física** (um profissional autônomo licenciando o plugin em nome próprio, por exemplo) — nesse caso, o domínio e o padrão de uso podem se tornar dado pessoal por associação ao nome/e-mail já cadastrado.

**Proposta de base legal para esse caso:** **legítimo interesse** (Art. 7º, IX, LGPD), pela necessidade operacional de controlar a cota contratada e de oferecer suporte técnico — sujeito ao teste de proporcionalidade e balanceamento que a LGPD exige para essa base, o que cabe à revisão jurídica confirmar.

## O campo de usuário WordPress

O cadastro de cliente reserva um campo para vincular o registro a um usuário do WordPress (`wp_user_id`), mas **nenhum fluxo do sistema usa esse campo hoje** — ele existe, vazio, para uma integração futura. Não há, portanto, tratamento adicional de dado de conta de usuário a descrever nesta versão.

## Envio a terceiros

Hoje o V3RLicense **não envia** os dados de cliente, licença ou ativação a nenhum serviço externo — não há integração de e-mail transacional, webhook ou API de terceiro que os leve para fora do próprio banco de dados do servidor.

## Retenção

{: .warning }
> **Pendente de decisão do dono do produto.** Não há, hoje, prazo de
> retenção definido nem rotina de expurgo automático — um registro de
> cliente, licença ou ativação permanece indefinidamente, mesmo depois que
> a licença associada é revogada ou expira. É preciso decidir: por quanto
> tempo manter esse histórico (considerando também eventual obrigação
> fiscal/contábil sobre uma venda), e se cabe expurgo ou anonimização
> automática depois de um prazo.

## Direitos do titular, e uma limitação real

O titular (a pessoa de contato cadastrada, ou o representante da organização) tem os direitos previstos na LGPD — confirmação, acesso, correção, eliminação, portabilidade, entre outros.

{: .important }
> **Limitação encontrada no sistema:** a tela de Clientes **recusa a
> exclusão** de um cliente que ainda tem alguma licença vinculada — o
> sistema não apaga em cascata. Isso significa que, hoje, um pedido de
> eliminação de um cliente com histórico de licença **não pode ser
> atendido apagando o registro**; a única via disponível é editar
> nome/e-mail para retirar o dado identificável, o que não é o mesmo que
> excluir. **Isso é uma lacuna a resolver** — o produto ainda não tem um
> caminho de anonimização, e a revisão jurídica precisa decidir como tratar
> um pedido de eliminação nesse cenário até que exista um.

Correção, acesso e portabilidade dos dados de contato são atendidos manualmente pela equipe operadora, editando o cadastro em **[Cadastrar cliente](/processos/cadastrar-cliente/)**.

## Segurança

- O acesso ao painel administrativo do V3RLicense é restrito a quem tem capacidade de administração no WordPress que o hospeda.
- Tokens de publicação e a chave de assinatura das respostas do servidor não são dado pessoal, mas seguem prática equivalente de segredo — nunca expostos em log ou e-mail.

---

## Alterações nesta Política

Esta é uma minuta. A versão vigente, quando revisada e aprovada, estará disponível em [docs.v3rlicense.v3rtech.com.br/legal/privacidade](https://docs.v3rlicense.v3rtech.com.br/legal/privacidade/).

---

## Contato

- **DPO da V3RTECH:** [dpo@v3rtech.com.br](mailto:dpo@v3rtech.com.br) — *a confirmar se este é também o contato correto para pedido de titular relativo ao V3RLicense especificamente.*

---

*Versão 0.1 (minuta) — Agosto de 2026. Documento não revisado juridicamente; não substitui a assessoria jurídica que a V3RTECH deve buscar antes de publicar esta política como vigente.*
