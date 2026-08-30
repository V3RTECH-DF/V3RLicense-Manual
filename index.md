---
title: Início
nav_order: 1
---

<img src="/assets/logo.svg" alt="V3RLicense — Gestão de licenças dos plugins WordPress da V3RTECH e da RIT" width="360" style="max-width:100%;height:auto;margin:0 0 12px">

# Manual do V3RLicense
{: .fs-8 }

**O servidor de licenças que emite, valida e distribui atualização para todos os plugins WordPress da V3RTECH e da RIT.**
{: .fs-6 .fw-300 }

Este manual é para a equipe da V3RTECH e da RIT, em dois papéis: quem **opera** o V3RLicense (emite licença, cadastra produto, gera token de publicação, resolve o chamado de "meu plugin não atualiza") e quem **desenvolve** um plugin da casa e precisa prepará-lo para o licenciamento e a auto-atualização. Não é para o cliente que instalou um plugin — esse nunca entra aqui; o que ele precisa saber mora na aba de licença do próprio plugin.

{: .note }
> **Uma exceção:** a página **[Como funciona a licença](/como-funciona/)** descreve a política de licenciamento em si — o que uma licença dá direito, o que acontece quando vence, como funciona a isenção RIT, e o que o cliente vê e resolve sozinho na aba "Minhas licenças" da própria conta. Essa página é a referência que os manuais dos outros plugins apontam quando o cliente final quer entender a própria licença.

[Primeiros passos](/primeiros-passos/){: .btn .btn-primary .mr-2 }
[Como funciona a licença](/como-funciona/){: .btn }

---

## Como faço…

<div class="grid" markdown="1">

- **[…emitir uma licença?](/processos/emitir-licenca/)**
- **[…cadastrar um produto para vender na loja?](/processos/cadastrar-produto-vendavel/)**
- **[…emitir uma isenção RIT?](/processos/emitir-isencao/)**
- **[…renovar uma licença vencida?](/processos/renovar-licenca/)**
- **[…revogar uma licença?](/processos/revogar-licenca/)**
- **[…liberar uma ativação para o cliente trocar de domínio?](/processos/liberar-ativacao/)**
- **[…publicar uma versão nova?](/processos/publicar-uma-versao/)**
- **[…o cliente diz que o plugin não atualiza — o que eu confiro?](/processos/diagnostico-sem-atualizacao/)**

</div>

Veja o índice completo em **[Como faço…](/processos/)**.

---

## Por onde começar

- **[Primeiros passos](/primeiros-passos/)** — o painel, a instalação e a primeira licença emitida, ponta a ponta.
- **[Como funciona a licença](/como-funciona/)** — a política de licenciamento, para explicar ao cliente ou para consulta rápida.
- **[Como faço…](/processos/)** — uma página por tarefa do dia a dia.
- **[Telas do painel](/modulos/)** — referência de campo por campo de cada aba.
- **[Preparar um plugin para o V3RLicense](/integrar-plugin/)** — para quem desenvolve: como integrar um plugin novo ou existente ao licenciamento e à auto-atualização.
- **[Novidades](/novidades/)** — o que mudou a cada versão, em linguagem simples.
- **[Perguntas Frequentes](/faq/)** — as dúvidas que mais aparecem.

---

## O que o V3RLicense faz

- **Emite e controla licenças** — por cliente, cobrindo um produto ou vários (marcados um a um, ou seguindo uma [lista de acesso](/processos/gerenciar-lista-acesso/)), com tipo (mensal, anual, perpétua…), origem (venda, cortesia, isenção…) e limite de ativações por produto.
- **Vende pela loja WooCommerce** — um [produto vendável](/processos/cadastrar-produto-vendavel/) publicado na loja emite a licença sozinho quando o pedido é pago, manda a chave por e-mail, e — no caso de assinatura — renova a mesma licença a cada cobrança seguinte. Licença vencida sem pagamento entra em carência antes de ser suspensa; veja **[Como funciona a licença](/como-funciona/)**.
- **Valida a licença do lado do plugin cliente** — o endpoint que cada plugin consulta para saber o próprio status, sem nunca travar o plugin por causa disso.
- **Controla ativação por domínio** — cada site em que o plugin roda conta como uma ativação; ambientes de teste não contam.
- **Distribui atualização** — o mesmo mecanismo que o WordPress usa para plugins do repositório oficial, mas para os nossos: verifica versão nova, entrega o changelog, libera o download.
- **Publica release** — normalmente sozinho, quando quem desenvolve empurra uma tag no repositório do plugin (a pipeline publica por token); manualmente pela tela é o caminho de exceção. Os dois passam pela mesma conferência tripla, que impede publicar pacote trocado.

{: .note }
> **Versão instalada:** `v0.16.1`. Este manual descreve o que existe **hoje**. Um dashboard de métricas de negócio ainda não foi construído; quando existir, este manual é atualizado.

---

<small>© 2026 [V3RTECH](https://v3rtech.com.br). Uso interno V3RTECH/RIT.</small>
