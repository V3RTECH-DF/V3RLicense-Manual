---
title: Como funciona a licença
nav_order: 3
---

# Como funciona a licença

Esta página é a **referência canônica** da política de licenciamento da V3RTECH e da RIT. Os manuais de cada plugin (V3REvent, V3RHelp, V3RLGPD, GE Associados, RIT360 Solidário, RIT360 Premiado…) apontam para cá quando o cliente final tem dúvida sobre a própria licença — é aqui, e só aqui, que a política vive por escrito.

## Por que isto importa

Quem opera o V3RLicense precisa entender a política com precisão para responder o cliente sem inventar, e para não prometer nem negar algo que o sistema não faz. É também o texto que você copia (ou linka) quando um cliente pergunta "por que perdi acesso?" ou "por que não perdi?".

## O que a licença dá direito

A licença de um plugin da V3RTECH/RIT dá direito a **atualização e correção** — não a uma funcionalidade extra dentro do plugin. Os plugins são distribuídos sob **GPL** (veja **[Licença de Uso do Software](/legal/licenca/)**), o que significa que o código já pertence a quem o instalou; o que se vende é o serviço de manter esse código atualizado.

{: .important }
> **Licença vencida não desliga o plugin.** Quando uma licença expira ou é revogada, o plugin cliente **continua funcionando exatamente como antes** — nenhuma tela para de abrir, nenhum recurso é bloqueado. O que muda é que o plugin **para de receber atualização e correção** até a licença ser renovada.
>
> Isso é decisão de política, não limitação técnica: o endpoint que o plugin usa para saber o próprio status (`/validate`) sempre responde com sucesso, informando o status real (`active`, `expired`, `revoked`) — nunca nega a resposta por causa do status. Só os endpoints de atualização e download recusam quando a licença não está em dia, porque é exatamente isso que a licença cobre.

## Os três status de uma licença

| Status | O que significa | O que o plugin cliente sente |
|---|---|---|
| **Ativa** | dentro da validade, não revogada | atualização normal |
| **Expirada** | passou da data de validade | plugin funciona; atualização e download bloqueados até renovar |
| **Revogada** | cancelada manualmente (reembolso, fraude, decisão da casa) | plugin funciona; atualização e download bloqueados até nova decisão |

{: .note }
> **Revogação é decisão que só se desfaz emitindo outra coisa.** A tela de Licenças não tem um botão de "reverter revogação" — uma licença revogada permanece revogada. Se o motivo da revogação deixar de existir, a saída é **[emitir uma licença nova](/processos/emitir-licenca/)** ou, quando fizer sentido, ajustar o cadastro manualmente com apoio técnico.

## Ativação por domínio, e a cota

Cada site (domínio) em que o cliente ativa o plugin conta como **uma ativação**. A licença tem um limite (`activations_max`) — quando o produto não define um padrão, é ilimitado.

{: .tip }
> **Ambientes de teste não consomem cota.** O servidor reconhece automaticamente quando uma ativação vem de um ambiente de desenvolvimento ou homologação (por padrões do próprio domínio) e não soma essa ativação ao limite da licença. Isso existe para o cliente poder testar o plugin num site de staging sem gastar a cota da licença de produção — se você olhar a lista de ativações de uma licença e ver mais linhas do que o limite contratado, é provável que algumas sejam de teste (a coluna "Ambiente de teste" mostra isso). Os critérios exatos de reconhecimento não são públicos — não são um dado que o manual expõe.

Quando o cliente muda de domínio (staging virou produção, ou o site mudou de endereço) e a licença está no limite, é preciso **[liberar uma ativação](/processos/liberar-ativacao/)** antes de ele conseguir ativar no domínio novo.

## Renovação

Renovar uma licença expirada **reativa a mesma chave** — o cliente não recebe uma chave nova, e as ativações que ele já tinha continuam valendo, sem precisar reativar nada. Veja o passo a passo em **[Renovar uma licença](/processos/renovar-licenca/)**.

## Isenção para organizações filiadas à RIT

Organizações do terceiro setor filiadas à RIT recebem licença **gratuita** — sem passar por venda. Hoje isso é feito emitindo a licença pela origem "Isenção — filiada à RIT", com validade normalmente anual, **renovada manualmente** pela mesma tela de renovação. Não existe hoje verificação automática contra uma fonte externa de filiação — está registrado como funcionalidade futura (V3RLicense-Code#4). Veja o passo a passo em **[Emitir uma isenção](/processos/emitir-isencao/)**.

## Publicação de atualização

Quando uma versão nova de um plugin é publicada no V3RLicense, todo cliente com licença **ativa** daquele produto passa a ver o aviso de atualização no próprio wp-admin, do mesmo jeito que veria para um plugin do repositório oficial do WordPress. Cliente com licença expirada ou revogada não vê a atualização — mesmo que o plugin continue funcionando. Veja **[Publicar uma versão](/processos/publicar-uma-versao/)**.

## Glossário

**Ativação**
: Um domínio em que o cliente instalou e ativou o plugin com uma chave de licença. Conta contra a cota da licença, salvo ambiente de teste.

**Chave de licença** (`license_key`)
: O código que o cliente cola no campo de licença do plugin. Não muda ao longo da vida da licença — nem em renovação.

**Origem**
: O motivo de uma licença existir (venda, cortesia, isenção RIT…). Cadastro livre, sem regra de negócio própria — é rótulo, não lógica.

**Tipo de licença**
: A periodicidade (mensal, anual, perpétua…) usada para calcular a data de expiração na emissão e na renovação.

**Token de publicação**
: Credencial de máquina que publica release por API, sem passar pela tela — usada por pipeline de CI. Veja **[Gerenciar tokens de publicação](/processos/gerenciar-tokens-publicacao/)**.
