---
title: Clientes
parent: Telas do painel
nav_order: 4
---

# Clientes

Veja o passo a passo em **[Cadastrar cliente](/processos/cadastrar-cliente/)** e, para pedido de eliminação de dados, **[Anonimizar um cliente](/processos/anonimizar-cliente/)**.

![Lista de clientes com nome e e-mail de cada organização cadastrada](/assets/screenshots/clientes-lista.png)

## Colunas da listagem

Nome · E-mail.

## Campos do formulário

Nome · E-mail.

## Ações

Editar · **Anonimizar cliente** (desde a v0.38.0; um cliente por vez, sem lote) · Excluir (linha a linha e em lote).

{: .note }
> **Cliente que tem licença não pode ser excluído** (desde a v0.38.1), seja a licença ativa, vencida, revogada ou arquivada. A tela recusa, mostra quais são as licenças e oferece o botão **Anonimizar este cliente**. Nada é revogado nem apagado. Só cliente **sem nenhuma licença** pode ser excluído, com uma confirmação. Para eliminar os dados da pessoa **preservando o histórico da licença**, use **Anonimizar**: veja **[Anonimizar um cliente](/processos/anonimizar-cliente/)**.

**Excluir vários de uma vez.** Marque os clientes e use **Excluir selecionados**. A janela diz quantos serão excluídos e quantos serão recusados por terem licença. Ao final, o resultado separa **excluídos**, **recusados por regra** (os que têm licença) e **falhas**. Para os recusados, a tela oferece o atalho de anonimizar, um de cada vez.

Depois de anonimizado, o cadastro mostra **Anonimizado em** com a data, o nome e o e-mail de marcador, e deixa de oferecer Editar e Anonimizar.
