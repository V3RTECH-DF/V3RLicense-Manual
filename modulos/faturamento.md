---
title: Faturamento
parent: Telas do painel
nav_order: 12
---

# Faturamento

A visão gerencial do negócio: quanto entrou, o que está vencendo, e quem comprou e não implantou. Acessada pelo menu **V3RLicense → Faturamento**.

<!-- TODO (manual): capturar quando a loja tiver vendas reais. A tela vazia não ilustra nada — ver "Capturas pendentes" no fim desta página. -->

## Por que isto importa

Até aqui, responder "quanto faturamos este mês" ou "quais clientes não implantaram o que compraram" exigia cruzar a tela de Licenças com a de Ativações à mão. O Faturamento junta isso num só lugar, para decisão — não para conferência fiscal (para isso, o pedido no WooCommerce continua sendo a fonte).

## O que a tela mostra

- **Faturamento líquido do mês**, com o mês anterior ao lado para comparar.
- **Licenças emitidas por produto**, separando **venda** de **isenção**.
- **Receita por produto**.
- **Licenças a vencer** em 30, 60 e 90 dias — janelas **cumulativas**: quem vence em 30 dias também está contado em 60 e em 90.
- **Ativações por licença** — cota vendida contra sites realmente ativados.
- **Taxa de renovação**, mostrando os dois números que a compõem (quantas venceram no período e quantas dessas renovaram).
- **Licenças revogadas** — total corrente, não do mês.

## As regras que evitam ler o número errado

{: .important }
> **Cada evento entra no mês em que ele aconteceu.** Um estorno feito em setembro sobre uma venda de agosto reduz o faturamento de **setembro**, não o de agosto. Agosto fechado não muda depois de fechado. Se você reabrisse o mês passado a cada estorno, o número que você já reportou para alguém deixaria de bater — a tela protege isso de propósito.

{: .warning }
> **"Sem valor apurado" não é zero.** São licenças emitidas antes de o sistema passar a guardar quanto foi pago por elas. O faturamento do período pode ser **maior** do que o mostrado, na proporção de quantas licenças caem nesse balde. Não use o número da tela como faturamento definitivo enquanto houver licenças antigas nessa situação.

{: .warning }
> **"Sem origem informada" não entra em venda nem em isenção.** São licenças que não declaram se foram vendidas ou concedidas. Elas ficam de fora dos dois lados do gráfico "Licenças emitidas por produto" — não some para "venda" achando que é isenção, nem o contrário.

{: .note }
> **Revogação não tem data nem motivo guardados.** Por isso "Licenças revogadas" mostra o **total corrente** (todas as revogadas até hoje), e não quantas foram revogadas *neste* mês. A tela avisa isso; não tente ler como um número mensal.

## Ativações por licença: o indicador que antecipa perda

Cota de dez sites com um ativado é cliente que comprou e não implantou — e cliente que não implantou não renova. É o sinal mais barato de risco de churn que a tela oferece, porque aparece **antes** do vencimento, não depois.

{: .example }
> **Exemplo:** um cliente comprou uma licença para 10 sites e só ativou em 1. Isso não significa erro de cadastro — normalmente é um contrato de agência com cota reservada para clientes futuros. Mas se a cota reservada nunca é usada, é sinal de que vale uma ligação antes do vencimento, não de esperar a renovação para descobrir que ele não vai renovar.

{: .note }
> **Ambiente de teste não conta nessa contagem.** Um site marcado como ambiente de teste não é ativação "real" para efeito deste indicador — do mesmo jeito que não conta para o limite de ativações da licença em nenhuma outra tela.

## Quando dá errado

- **A tela está vazia** — normal enquanto a loja não vendeu nada; não é defeito.
- **Um número parece baixo demais** — confira se não é um mês com muita licença "sem valor apurado" ou "sem origem informada" antes de tratar como faturamento real caindo.
- **Taxa de renovação parece errada** — lembre que ela olha o período de vencimento, não o de renovação; uma licença vencida em agosto e renovada em setembro conta para agosto.

## Capturas pendentes

A tela ainda não tem dados (a loja não vendeu nada até o momento desta edição). Quando houver ao menos uma venda, valem estas capturas, em desktop:

- `faturamento-visao-geral.png` — a tela cheia, com faturamento do mês, comparação com o mês anterior, e os cartões de licenças a vencer.
- `faturamento-por-produto.png` — os gráficos de licenças emitidas por produto (venda × isenção) e receita por produto.
- `faturamento-ativacoes-renovacao.png` — ativações por licença e taxa de renovação lado a lado.
- `faturamento-avisos.png` — um recorte mostrando os avisos "sem valor apurado" ou "sem origem informada" em uso real (só se algum aparecer nos dados reais; não forçar isso artificialmente).
