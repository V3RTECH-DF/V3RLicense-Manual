---
title: Renovar uma licença
parent: Como faço…
nav_order: 6
---

# Renovar uma licença

## Por que isto importa

Renovar é o que devolve a uma licença expirada o direito a atualização e correção. É seguro fazer sem medo de "perder" algo do cliente: a chave não muda e as ativações continuam de pé — o cliente não precisa reativar nada nos domínios já ativos.

{: .note }
> **Licença de assinatura recorrente já se renova sozinha** a cada cobrança paga na loja — a mesma licença é estendida automaticamente, sem passar por aqui. Esta página serve para o resto: isenção/cortesia (sempre manual, veja **[Configurações](/modulos/configuracoes/)**), venda avulsa e qualquer licença que a cobrança automática não alcançou.

## Passo a passo

1. Abra a aba **Licenças** e localize a licença (filtre por status "Expirada", produto ou cliente).
2. Clique no ícone **Renovar licença** na linha dela.
3. Confirme no diálogo.
4. A nova data de expiração aparece na coluna "Expira em".

## Exemplo

Uma licença anual do produto "V3REvent" expirou em 15/07/2026. O cliente pagou a renovação em 20/08/2026 (com atraso). Ao renovar, a nova expiração é calculada a partir de **hoje** (20/08/2026 + 12 meses), não a partir da data antiga de vencimento — porque a renovação está atrasada. Se o mesmo pagamento tivesse chegado em 10/07/2026 (antes de vencer), a nova expiração seria calculada a partir de 15/07/2026, sem "perder" os dias que restavam.

{: .note }
> **A regra:** renovação em dia conta a partir do vencimento anterior; renovação atrasada conta a partir de hoje. Isso evita que o cliente ganhe tempo por atraso, e também evita que ele perca tempo por renovar antes do prazo.

## Renovar várias de uma vez

Quando várias licenças vencem juntas — o caso mais comum é uma leva de isenções RIT no mesmo mês —, renove todas de uma vez em vez de repetir o passo a passo uma por uma.

![Diálogo de confirmação da renovação em lote avisando que a seleção mistura licenças Trimestral e Mensal, e que os vencimentos resultantes serão diferentes entre elas](/assets/screenshots/renovar-lote-confirma-tipos-diferentes.png)

1. Na aba **Licenças**, filtre se quiser reduzir a lista, e marque as caixas de seleção das licenças a renovar (a caixa no cabeçalho marca a página inteira).
2. Clique em **Renovar selecionadas (N)**.
3. Leia a confirmação com atenção: se a seleção mistura licenças de **tipos diferentes** (por exemplo, uma Mensal e uma Trimestral), o diálogo avisa que os vencimentos resultantes serão diferentes entre elas — cada licença continua seguindo a própria regra (a mesma do item a item: em dia conta do vencimento anterior, atrasada conta de hoje), não uma data única para o lote.
4. Confirme. O resultado mostra quantas foram concluídas, quantas foram recusadas por regra (por exemplo, sem tipo de licença atribuído) e quantas falharam.

{: .tip }
> **Misturar tipos na mesma seleção não é errado** — só produz vencimentos diferentes, e é para isso que o aviso existe: para você decidir com essa informação em mãos, não descobrir depois olhando a coluna "Expira em".

## Dicas e armadilhas

- **O botão vem desabilitado** quando a licença não tem tipo de licença definido (licenças muito antigas, emitidas antes desse cadastro existir) ou já está revogada. Nesse caso, é preciso atribuir um tipo a ela antes — apoio técnico.
- **Não confunda com reemissão** — renovar reaproveita tudo (chave, ativações); emitir uma licença nova cria tudo do zero e obriga o cliente a trocar a chave no plugin. Prefira sempre renovar.

## Quando dá errado

- **Botão desabilitado sem explicação visível** — confira se a licença tem tipo de licença atribuído; se não tiver, é preciso apoio técnico para atribuir um antes de renovar.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel renova qualquer licença.
