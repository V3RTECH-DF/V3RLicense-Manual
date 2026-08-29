---
title: Listas de acesso
parent: Telas do painel
nav_order: 9
---

# Listas de acesso

Veja o passo a passo em **[Gerenciar listas de acesso](/processos/gerenciar-lista-acesso/)** e **[Emitir uma licença](/processos/emitir-licenca/)**.

![Tela Listas de acesso: formulário "Nova lista de acesso" e uma linha "acesso_total" / "Acesso total (parceria)" cobrindo V3RLGPD e V3RHelp!, seguida por 1 licença, status Ativa](/assets/screenshots/listas-de-acesso.png)

Uma lista de acesso é um conjunto nomeado de produtos. Uma licença pode **seguir** uma lista em vez de ter os produtos marcados um a um — nesse caso, a cobertura dela acompanha a lista: produto acrescentado à lista passa a valer, na hora, para toda licença que a segue.

## Colunas da listagem

| Coluna | O que mostra |
|---|---|
| Identificador | slug, travado depois de criado |
| Rótulo exibido | nome mostrado no formulário de emissão |
| Produtos cobertos | os produtos que compõem a lista hoje |
| Licenças seguindo | quantas licenças estão vinculadas a esta lista |
| Status | Ativa (aparece na emissão) / Inativa |

## Campos do formulário de criação

Identificador (slug) · Rótulo exibido · Ativa (aparece na emissão de licença).

A lista nasce sem produto — produtos são acrescentados depois, pelo painel de gestão da lista (ícone de lista de tarefas na coluna Ações).

## Painel de produtos da lista

![Modal "Produtos de 'Acesso total (parceria)'" com a seção Nesta lista (V3RLGPD, V3RHelp!, cada um com botão Remover) e Disponíveis para acrescentar (V3RProp, com botão Acrescentar)](/assets/screenshots/listas-de-acesso-produtos.png)

Abre a partir do ícone de lista de tarefas na linha da lista. Duas seções:

- **Nesta lista** — produtos cobertos hoje, com **Remover**.
- **Disponíveis para acrescentar** — produtos ainda de fora, com **Acrescentar**.

{: .important }
> **Acrescentar produto estende a cobertura na hora**, para toda licença que segue a lista. **Remover produto não tira a cobertura de quem já a tem** — só impede que licenças futuras a recebam. Veja o detalhe em **[Gerenciar listas de acesso](/processos/gerenciar-lista-acesso/)**.

## Ações

Editar rótulo/status · Gerenciar produtos (o painel acima) · Excluir (recusado quando alguma licença segue a lista).
