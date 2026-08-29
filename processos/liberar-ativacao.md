---
title: Liberar uma ativação
parent: Como faço…
nav_order: 8
---

# Liberar uma ativação

## Por que isto importa

Cada domínio em que o cliente ativa o plugin consome uma vaga — contada **por produto**, não pela licença inteira. Quando o cliente troca de domínio, migra de staging para produção, ou simplesmente atingiu o limite de um dos produtos cobertos, ele não consegue ativar aquele produto num site novo até alguém liberar uma vaga aqui. É uma das dúvidas mais comuns — "por que meu plugin diz que a licença já está em uso em outro lugar".

## Passo a passo

1. Na aba **Licenças**, localize a licença do cliente e clique no ícone **Ver ativações**.
2. Se a licença cobrir mais de um produto, use o **filtro por produto** para ver só as ativações do plugin em questão — a cota daquele produto aparece ao lado do filtro.
3. Na lista de ativações, identifique o domínio que não é mais usado (site antigo, staging que já cumpriu o papel, domínio errado ativado por engano).
4. Clique no ícone **Desativar domínio** na linha correspondente.
5. Confirme — a mensagem nomeia o domínio e o produto: "`institutovidanova.org.br` (V3REvent) deixará de contar como ativação desta licença. Ele poderá reativar depois, se necessário."
6. Avise o cliente que ele já pode ativar no domínio novo.

Para liberar várias de uma vez: marque as caixas e use **Desativar selecionadas (N)**.

## Exemplo

O cliente "Instituto Vida Nova" tinha a licença do V3REvent limitada a 1 ativação, usada em `institutovidanova.org.br`. Ele migrou para um domínio novo (`ivn.org.br`) e agora recebe erro de limite atingido ao tentar ativar. Você abre a licença dele, vê a ativação antiga em `institutovidanova.org.br` (que não responde mais desde a migração), desativa essa linha, e o cliente ativa normalmente no domínio novo.

## Dicas e armadilhas

{: .tip }
> **Confira a coluna "Ambiente de teste" antes de desativar.** Ativações marcadas como teste **não contam** na cota — se o cliente está no limite mesmo tendo uma linha de teste na lista, o problema não é aquela linha; é preciso olhar as ativações que não são de teste.

- **"Último contato" ajuda a identificar o que está obsoleto.** Um domínio que não fala com o servidor há meses provavelmente foi desativado ou substituído do lado do cliente — mas confirme com ele antes de desativar algo que ainda pode estar em uso.
- **Desativar não é permanente** — o mesmo domínio pode reativar depois, se precisar. Não é uma decisão de risco alto como revogar uma licença inteira.
- **Licença cobrindo mais de um produto: o mesmo domínio pode aparecer mais de uma vez na lista**, uma linha por plugin que ele ativou. A coluna Produto (ou o filtro aplicado) diz qual é qual — confira antes de desativar, porque desativar a linha errada libera a vaga do produto errado. Veja **[Ativações](/modulos/ativacoes/)**.

## Quando dá errado

- **Checkbox de seleção não aparece numa linha** — a ativação já está desativada; não há ação a fazer nela.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel libera ativação de qualquer licença.
