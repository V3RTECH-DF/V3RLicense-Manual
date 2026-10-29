---
title: Revogar uma licença
parent: Como faço…
nav_order: 7
---

# Revogar uma licença

## Por que isto importa

Revogar é a ação para reembolso, fraude ou qualquer decisão de cancelar uma licença por definitivo. É diferente de deixar vencer: uma licença revogada fica marcada como revogada mesmo que a data de expiração ainda esteja no futuro, e **não existe um botão para desfazer**.

Desde a v0.37.0, toda revogação guarda **o motivo e a data**. É isso que permite, meses depois, responder "por que esta licença foi revogada?" sem depender da memória de quem clicou — e que o **[Faturamento](/modulos/faturamento/)** conte as revogadas mês a mês.

{: .important }
> **O plugin do cliente continua funcionando depois de revogado.** Revogar não desliga o plugin — só impede atualização e download, igual a uma licença expirada (veja **[Como funciona a licença](/como-funciona/)**). Não use "revogar" pensando em bloquear o uso do plugin: isso não é o que a ação faz, nem o que a política da casa prevê.

## Passo a passo

**Uma licença ou acesso:**
1. Na aba **Licenças e acessos**, localize a linha.
2. Clique no ícone **Revogar licença** (ou **Revogar acesso**, se a Categoria da linha for Acesso) na linha dela.
3. Leia o aviso — "Esta licença deixará de validar/atualizar. A ação não pode ser desfeita pela tela".
4. Em **Motivo da revogação**, escolha o que melhor descreve a decisão (veja a tabela abaixo). A opção que já vem marcada é **Revogação manual**.
5. Se quiser, escreva em **Observação (opcional)** o detalhe que o motivo não carrega — número do pedido, quem autorizou. Cabem até 500 caracteres.
6. Clique em **Revogar**.

![Janela de confirmação "Revogar licença", com o aviso de que a ação não pode ser desfeita pela tela, o campo Motivo da revogação preenchido com Revogação manual e o campo Observação (opcional)](/assets/screenshots/licencas-revogar-motivo.png)

**Várias de uma vez:**
1. Marque as caixas de seleção das licenças/acessos a revogar (ou "selecionar todas").
2. Clique em **Revogar selecionadas (N)**.
3. Confirme — o diálogo mostra quantas serão afetadas, e pede o motivo e a observação uma vez só: **valem para todas as selecionadas**. Se os motivos são diferentes, revogue em grupos separados.
4. O resultado mostra três números: concluídas, recusadas por regra e falhas — confira que bate com o que você esperava, principalmente se algum item foi recusado.

### Os quatro motivos

| Motivo | Quando usar |
|---|---|
| **Estorno total do pedido** | O dinheiro voltou ao cliente e a licença deixou de ter razão de existir. |
| **Pedido cancelado** | O pedido foi cancelado depois de pago. |
| **Revogação manual** | Decisão da casa: fraude, uso indevido, pedido do cliente. |
| **Outro** | Nenhum dos anteriores serve — explique na **Observação**. |

A lista é fechada de propósito: com motivos escritos à mão, nenhum relatório consegue agrupar "estorno" e "estornado" como a mesma coisa.

### O que a lista mostra depois

Na coluna **Status**, a licença revogada ganha uma linha abaixo do selo: o motivo e a data ("Estorno total do pedido · em 27/10/2026") e, se você escreveu, a observação.

![Lista de licenças com três revogadas: uma com motivo e data, uma com "Pedido cancelado" e a data, e uma com a mensagem "Data e motivo não registrados"](/assets/screenshots/licencas-lista-revogacao-envio.png)

{: .note }
> **"Data e motivo não registrados"** aparece nas licenças revogadas **antes da v0.37.0**. Não é defeito: naquela época o sistema não guardava nenhum dos dois, e inventar um valor seria pior que admitir que não se sabe. Essas licenças não entram na contagem mensal do Faturamento.

## Quando a revogação acontece sozinha

Você não precisa revogar à mão nestes dois casos — a licença é revogada automaticamente, já com o motivo certo:

- **Estorno total do pedido** na loja → motivo **Estorno total do pedido**. Estorno **parcial** não revoga: costuma ser ajuste de valor, não desistência.
- **Pedido pago que é cancelado** → motivo **Pedido cancelado**.

{: .warning }
> **Cancelar a assinatura não revoga nada.** O cliente mantém o acesso até o fim do período que já foi pago; só deixa de haver cobrança seguinte. Também não revoga o cancelamento de um pedido de **renovação** que não foi pago — isso é "não renovar", e a licença vence na data dela. E pedido que nunca chegou a ser pago (pendente ou malsucedido que vira cancelado) é ignorado: não havia licença emitida.

{: .note }
> **Revogar um acesso revoga o token dele junto**, automaticamente, dentro de até 1 hora — sem precisar de uma segunda ação em **[Gerenciar tokens de serviço](/processos/gerenciar-tokens-de-servico/)**.

## Exemplo

Um pedido foi estornado pelo cliente 10 dias depois da compra. A licença correspondente (produto "RIT360 Solidário", cliente "Fulano de Tal") deve ser revogada para não continuar recebendo atualização — mesmo que a validade anual só vencesse em 8 meses.

## Dicas e armadilhas

- **Não há desfazer pela tela.** Se revogou por engano, a saída é **[emitir uma licença nova](/processos/emitir-licenca/)** para o mesmo cliente — o que obriga o cliente a trocar a chave no plugin dele. Confirme antes de revogar.
- **Escolha o motivo certo, não o que já vem marcado.** Deixar tudo em "Revogação manual" por preguiça apaga a diferença entre fraude, estorno e cancelamento — justamente o que o motivo existe para guardar. A consequência aparece quando alguém pergunta quantas revogações do trimestre foram por estorno, e ninguém sabe responder.
- **Não cole dado pessoal na Observação.** O campo é livre e fica gravado; escreva "estorno do pedido 1842", não o nome nem o telefone do cliente.
- **Em lote, leia o resultado, não só o "concluído".** "Recusados por regra" e "falhos" não aparecem sozinhos — se você esperava revogar 10 e o resultado mostra 8 concluídas e 2 recusadas, algo precisa de atenção antes de considerar a tarefa terminada.

## Quando dá errado

- **Ícone de revogar desabilitado** — a licença já está revogada; não há nada a fazer.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel revoga qualquer licença. Justamente por isso, e por não ter desfazer, trate como ação que merece confirmação de verdade antes de clicar, não como rotina automática.
