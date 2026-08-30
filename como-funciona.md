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

Uma mesma chave de licença pode cobrir **mais de um plugin** — é o caso de organizações parceiras ou filiadas à RIT com direito ao catálogo inteiro. Nesse caso, a mesma chave é colada em cada um dos plugins cobertos. Status, expiração e renovação são da **licença como um todo** — vencer ou revogar afeta todos os plugins cobertos ao mesmo tempo. Só a cota de ativação é diferente: ela é contada **separadamente para cada plugin coberto** (veja a seção seguinte).

{: .important }
> **Licença vencida não desliga o plugin.** Quando uma licença expira ou é revogada, o plugin cliente **continua funcionando exatamente como antes** — nenhuma tela para de abrir, nenhum recurso é bloqueado. O que muda é que o plugin **para de receber atualização e correção** até a licença ser renovada.
>
> Isso é decisão de política, não limitação técnica: o endpoint que o plugin usa para saber o próprio status (`/validate`) sempre responde com sucesso, informando o status real (`active`, `expired`, `revoked`) — nunca nega a resposta por causa do status. Só os endpoints de atualização e download recusam quando a licença não está em dia, porque é exatamente isso que a licença cobre.

## A venda pela loja emite a licença sozinha

Um [produto vendável](/processos/cadastrar-produto-vendavel/) publicado na loja WooCommerce não precisa de ninguém do lado do V3RLicense para virar licença — o pedido pago é que dispara tudo:

- **Compra avulsa** (produto de licença perpétua) — pedido pago emite **uma licença por unidade comprada**, e o V3RLicense manda a chave ao cliente por e-mail. Comprou 3, o cliente recebe 3 chaves.
- **Assinatura** (produto de licença mensal, trimestral, semestral ou anual) — o pagamento inicial emite a licença do mesmo jeito; cada cobrança de renovação seguinte **estende essa mesma licença** — mesma chave, mesmas ativações preservadas — em vez de criar uma segunda. O cliente não reconfigura nada a cada cobrança, e a renovação automática não manda e-mail (o próprio WooCommerce já confirma a cobrança).

Em ambos os casos o cliente é sempre identificado pela **conta com que fez o pedido** na loja, nunca por um e-mail digitado à parte.

## Os cinco status de uma licença

| Status | O que significa | O que o plugin cliente sente |
|---|---|---|
| **Ativa** | dentro da validade, não revogada | atualização normal |
| **Em carência** | venceu, mas dentro dos 15 dias seguintes ao vencimento — só para licença que **gera cobrança** | atualização normal, como se ainda estivesse ativa |
| **Suspensa por falta de pagamento** | venceu e passou dos 15 dias de carência, sem renovar — só para licença que gera cobrança | plugin funciona; atualização e download bloqueados até renovar |
| **Expirada** | venceu e a origem **não gera cobrança** (licença concedida) — vai direto para expirada, sem carência | plugin funciona; atualização e download bloqueados até renovar |
| **Revogada** | cancelada manualmente (reembolso total, fraude, decisão da casa) | plugin funciona; atualização e download bloqueados até nova decisão |

{: .note }
> **Revogação é decisão que só se desfaz emitindo outra coisa.** A tela de Licenças não tem um botão de "reverter revogação" — uma licença revogada permanece revogada. Se o motivo da revogação deixar de existir, a saída é **[emitir uma licença nova](/processos/emitir-licenca/)** ou, quando fizer sentido, ajustar o cadastro manualmente com apoio técnico.

## Carência e suspensão — só para quem paga

![Lista de licenças mostrando os cinco status lado a lado: Ativa, Suspensa por falta de pagamento, Revogada, Expirada e Em carência](/assets/screenshots/licencas-status-novos.png)

Uma licença vencida não vira "suspensa" automaticamente — o que acontece depende de a **origem** dela [gerar cobrança ou não](/modulos/origens/):

- **Origem que gera cobrança** (ex.: "Venda (WooCommerce)") — a licença vencida entra em **carência por 15 dias corridos**, contados do vencimento. Durante a carência, o plugin do cliente continua recebendo atualização normalmente, como se a licença estivesse ativa. Passados os 15 dias sem renovar, a licença vira **suspensa por falta de pagamento**.
- **Origem que não gera cobrança** (ex.: "Isenção — filiada à RIT") — vence e vira **expirada** direto, sem carência nenhuma. Faz sentido: não há cobrança pendente para dar tempo de regularizar.

{: .important }
> **Suspensa não derruba nada no site do cliente.** É a mesma regra de sempre para licença sem cobertura: o plugin já instalado continua funcionando normalmente — só para de receber novas versões e correções. `activate`/`validate` continuam liberados; só atualização e download ficam bloqueados.

Regularizar o pagamento — pela renovação manual, pela [renovação em lote](/processos/renovar-licenca/), ou pela cobrança automática de uma assinatura — devolve a licença a "Ativa" na hora, porque o status é sempre recalculado a partir da data de vencimento, nunca depende de um processo agendado ter rodado.

### Estorno

O WooCommerce dispara o mesmo evento para estorno total e parcial; o que diferencia um do outro é o pedido ter ficado **inteiramente** reembolsado ou não:

- **Estorno total** — revoga a licença.
- **Estorno parcial** — não mexe na licença. Um desconto ou ajuste parcial no pedido não tira a cobertura do cliente.

Cancelamento de assinatura, por si só, **não revoga nada**: o cliente mantém o acesso normal até o fim do período que já foi pago.

## Avisos automáticos por e-mail

O V3RLicense avisa por conta própria, sem que o operador precise lembrar de nada. A régua muda conforme o tipo de cobrança da licença:

**Antes do vencimento**, ao cliente de uma licença comprada:

| Tipo de licença | Antecedência dos avisos |
|---|---|
| Mensal | 7 e 1 dia antes |
| Trimestral | 15, 7 e 1 dia antes |
| Semestral e Anual | 30, 15, 7 e 1 dia antes |
| Vitalícia/Perpétua | nenhum aviso — nunca vence |

**Assinatura recorrente ativa** foge dessa régua: o cliente recebe **um aviso só**, sempre 7 dias antes da cobrança automática — a régua completa faria pouco sentido para quem paga sozinho, sem precisar agir.

**Durante a carência** (só licença que gera cobrança), o cliente recebe mais avisos: um no dia em que a carência começa, um quando faltam 8 dias para a suspensão, um no último dia do prazo, e um quando a suspensão de fato acontece.

**Licença concedida** segue outra regra por completo: **quem é avisado é o operador, nunca o cliente**, porque a renovação dessas licenças é sempre manual. O e-mail vai para o endereço cadastrado em **[Configurações](/modulos/configuracoes/)**, na mesma antecedência da tabela acima, e sugere usar a renovação em lote.

{: .note }
> **A régua roda mesmo sem loja.** Ela usa o agendador do próprio WordPress, não o mecanismo do WooCommerce — continua funcionando mesmo para licença vendida fora da loja (sem pedido vinculado) ou se a loja for desativada. O que decide se uma licença entra na régua é a origem estar marcada como "gera cobrança", nunca a existência de um pedido.

### Identidade visual e remetente

Desde a v0.13.1, todo e-mail que o cliente recebe — chave da licença, avisos de vencimento e de carência, e o aviso ao operador de uma licença concedida — usa a identidade visual institucional da V3RTECH: logomarca no cabeçalho, títulos em verde escuro, e a chave da licença destacada num bloco amarelo para não passar despercebida no meio do texto. O conteúdo e o comportamento continuam os mesmos de sempre — só a aparência mudou.

Os e-mails que o **WooCommerce** manda por conta própria (confirmação de pedido, recibo, ao cliente que compra pela loja) ganharam a mesma identidade, para o cliente não notar dois visuais diferentes numa mesma compra.

**Isso também mudou para quem opera:** os avisos que o WooCommerce manda ao **administrador da loja** — novo pedido, pedido cancelado, pedido malsucedido, gateway de pagamento ativado, e os seis avisos de assinatura (nova cobrança de renovação, assinatura trocada, cancelada, expirada, suspensa e reativada) — passaram a ir para `comercial@v3rtech.com.br`. Antes, quatro desses avisos iam para `suporte@v3rtech.com.br` por configuração explícita, e os outros seis caíam lá por herdarem o e-mail de administração do WordPress (que continua sendo `suporte@`). **Quem acompanhava pedido novo pela caixa do suporte precisa passar a olhar `comercial@`.** O remetente dos e-mails da loja também passou a ser `comercial@v3rtech.com.br`, no lugar de `suporte@`.

{: .important }
> Os e-mails que o **V3RLicense** manda diretamente (chave, vencimento, carência, aviso ao operador de isenção) já saíam como `V3RTECH <comercial@v3rtech.com.br>`, e continuam assim — o remetente deles é definido pelo próprio plugin, não pela configuração da loja nem pelo padrão do WordPress. O que mudou de remetente foram os e-mails nativos da **loja WooCommerce**, que agora saem do mesmo endereço.

## Ativação por domínio, e a cota

Cada site (domínio) em que o cliente ativa um plugin conta como **uma ativação**, com um limite (`activations_max`) — quando o produto não define um padrão, é ilimitado. Para uma licença que cobre mais de um plugin, esse limite é **contado separadamente para cada plugin**: ativar o V3RLGPD num domínio não usa a cota do V3RHelp! coberto pela mesma chave.

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
