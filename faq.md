---
title: Perguntas Frequentes
nav_order: 6
---

# Perguntas Frequentes

{: .note }
> Este é um painel interno, sem mecanismo de feedback do usuário final. As perguntas abaixo vêm dos comportamentos mais fáceis de interpretar errado, confirmados no código — não são inventadas, mas também não são um recorte de dúvidas reais registradas em algum canal (que este produto ainda não tem).

## A licença do cliente venceu. O plugin dele parou de funcionar?

Não. Licença vencida ou revogada nunca desliga o plugin — o que para é a atualização e o download de novas versões. Veja **[Como funciona a licença](/como-funciona/)**.

## Por que o cliente tem mais ativações na lista do que o limite da licença?

Provavelmente algumas são de ambiente de teste — essas não contam na cota. Confira a coluna "Ambiente de teste" em **Ver ativações**.

## Renovei a licença. O cliente precisa colar uma chave nova no plugin?

Não. Renovar reaproveita a mesma chave e preserva as ativações já existentes — o cliente não faz nada do lado dele.

## Emiti uma licença e agora tenho dois clientes parecidos na lista de Clientes. O que houve?

O e-mail informado na emissão provavelmente não bateu exatamente com o cliente já cadastrado (maiúscula, espaço, domínio diferente) — o sistema criou um cliente novo em vez de vincular ao existente. Veja **[Cadastrar cliente](/processos/cadastrar-cliente/)**.

## Um token de publicação rotulado "só para o produto X" pode publicar release de outro produto?

Não. Desde a v0.6.0, o token só publica o produto escolhido na criação (ou "Todos os produtos", se foi atribuído esse escopo mais permissivo) — o rótulo deixou de ser a única garantia. Veja **[Gerenciar tokens de publicação](/processos/gerenciar-tokens-publicacao/)**.

## O cliente diz que o plugin não recebe a atualização, mas a licença está ativa. E agora?

Confira o PHP do site dele. Desde 27/08/2026 todos os plugins da casa exigem PHP 8.2 — um site abaixo disso não recebe a atualização, e o WordPress não avisa por quê. Veja o roteiro completo em **[Diagnóstico: cliente diz que não atualiza](/processos/diagnostico-sem-atualizacao/)**.

## Revoguei uma licença por engano. Tem como desfazer?

Não pela tela. A saída é emitir uma licença nova para o mesmo cliente — o que exige que ele troque a chave no plugin. Veja **[Revogar uma licença](/processos/revogar-licenca/)**.

## Uma licença pode cobrir mais de um plugin?

Sim. Ao emitir, escolha "Segue uma lista de acesso" (a cobertura acompanha a lista, inclusive produtos acrescentados depois) ou "Produtos específicos" (cobertura fixa no que foi marcado na emissão). Veja **[Emitir uma licença](/processos/emitir-licenca/)**.

## Acrescentei um produto a uma lista de acesso. As licenças que já existiam recebem o produto na hora, ou só as próximas?

Na hora — todas as licenças que já seguem aquela lista passam a cobrir o produto novo imediatamente, sem nova emissão. Veja **[Gerenciar listas de acesso](/processos/gerenciar-lista-acesso/)**.

## Removi um produto de uma lista de acesso. Quem já tinha acesso perde na hora?

Não. Remover de uma lista só impede que licenças futuras recebam aquele produto ao seguir a lista — quem já tinha o acesso continua com ele. Para tirar o acesso de um cliente específico, é preciso agir na licença dele, não na lista.

## Organizações filiadas à RIT têm renovação automática da isenção?

Não hoje. A validade é controlada manualmente, do mesmo jeito que qualquer licença anual — está registrado como funcionalidade futura. Veja **[Emitir uma isenção RIT](/processos/emitir-isencao/)**.

## Uma licença ficou "Suspensa por falta de pagamento". O que eu faço?

Renove — individualmente ou pela **[renovação em lote](/processos/renovar-licenca/)**. Assim que a data de vencimento avança, a licença volta a "Ativa" na hora, e o plugin do cliente volta a receber atualização. Nada precisa ser reativado do lado dele: a chave e as ativações continuam as mesmas. Veja **[Como funciona a licença](/como-funciona/)** para a diferença entre "Em carência" e "Suspensa".

## Excluí o cadastro de um produto vendável. Ele sumiu da loja?

Não. Excluir aqui remove só o cadastro que liga o V3RLicense à loja — o produto que já foi publicado no WooCommerce continua existindo lá, com o preço, os pedidos e o histórico intactos. Veja **[Cadastrar um produto vendável](/processos/cadastrar-produto-vendavel/)**.

## Um pedido foi estornado. A licença é revogada automaticamente?

Só se o estorno for **total**. Estorno parcial (um desconto, um ajuste no pedido) não mexe na licença — o cliente mantém a cobertura normalmente. Veja **[Como funciona a licença](/como-funciona/)**.

## O cliente cancelou a assinatura. Ele perde o acesso na hora?

Não. Cancelar a assinatura não revoga nada — o cliente mantém o acesso normal até o fim do período que já foi pago, sem tratamento especial. Só deixa de haver cobrança seguinte.
