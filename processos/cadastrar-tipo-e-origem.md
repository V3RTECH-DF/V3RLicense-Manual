---
title: Cadastrar tipo de licença e origem
parent: Como faço…
nav_order: 2
---

# Cadastrar tipo de licença e origem

## Por que isto importa

Toda licença emitida precisa de um **tipo** (define a periodicidade e, com ela, a data de expiração) e uma **origem** (por que ela existe — venda, cortesia, isenção…). Os dois são cadastros simples, sem regra de negócio embutida: são o vocabulário que aparece nos formulários e nos relatórios, não lógica.

## Passo a passo — Tipo de licença

1. Abra a aba **Tipos de licença**.
2. Preencha:
   - **Identificador (slug)** — travado depois de criado.
   - **Rótulo exibido** — o que aparece no formulário de emissão.
   - **Unidade** — Dias, Meses, Anos ou **Perpétua (nunca expira)**.
   - **Duração** — quantas unidades (ex.: `12` com unidade "Meses" = licença anual). Desabilitado quando a unidade é Perpétua.
   - Marque **Ativo** se ele deve aparecer no formulário de emissão.
3. Salve.

{: .example }
> **Exemplo:** "Anual" — slug `anual`, unidade "Meses", duração `12`. "Vitalícia" — slug `vitalicia`, unidade "Perpétua", sem duração.

## Passo a passo — Origem

1. Abra a aba **Origens**.
2. Preencha:
   - **Identificador (slug)** — travado depois de criado.
   - **Rótulo exibido**.
   - **Gera cobrança** — marque se licença emitida por esta origem é vendida; deixe desmarcado para origem concedida (isenção, cortesia), sem pagamento.
   - Marque **Ativa** se ela deve aparecer no formulário de emissão.
3. Salve.

{: .example }
> **Exemplo — concedida:** "Isenção — filiada à RIT" — slug `rit_grant`, "Gera cobrança" desmarcado, ativa. Usada em **[Emitir uma isenção](/processos/emitir-isencao/)**.
>
> **Exemplo — cobrada:** "Venda (WooCommerce)" — slug `purchase`, "Gera cobrança" marcado, ativa. É a origem que a loja usa para toda licença emitida por uma compra.

{: .warning }
> **"Gera cobrança" não é sobre desconto ou preço** — isso continua sendo cupom na loja. É sobre o que acontece quando a licença vence: origem que gera cobrança entra em carência e pode ser suspensa por falta de pagamento; origem concedida vai direto para expirada, sem carência, e quem é avisado do vencimento é o operador, não o cliente. Veja **[Como funciona a licença](/como-funciona/)**.

## Dicas e armadilhas

- **"Ativo"/"Ativa" desmarcado não apaga o cadastro** — só tira da lista de opções na emissão de licença nova. Licenças já emitidas com aquele tipo/origem continuam mostrando o rótulo normalmente.
- **Slug travado** — mesmo cuidado da tela de Produtos: confira antes de salvar, porque corrigir depois exige recadastrar.
- **Duração e unidade viajam juntas na fórmula de expiração.** Errar a duração (por exemplo, `1` em vez de `12` para "Anual") não dá erro nenhum na hora de cadastrar — só aparece quando alguém emitir uma licença desse tipo e a data de expiração sair errada.

## Quando dá errado

- **Exclusão recusada** — tipo ou origem referenciado por alguma licença não pode ser excluído. A saída é desativar (desmarcar "Ativo"/"Ativa"), não excluir.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel cadastra os dois.
