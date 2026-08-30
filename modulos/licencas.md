---
title: Licenças
parent: Telas do painel
nav_order: 1
---

# Licenças

Veja o passo a passo em **[Emitir uma licença](/processos/emitir-licenca/)**, **[Renovar](/processos/renovar-licenca/)** (individual e em lote), **[Revogar](/processos/revogar-licenca/)** e **[Emitir uma isenção RIT](/processos/emitir-isencao/)**. Sobre a cobertura por lista, veja **[Gerenciar listas de acesso](/processos/gerenciar-lista-acesso/)** e **[Listas de acesso](/modulos/listas-de-acesso/)**. Sobre os status de carência e suspensão, veja **[Como funciona a licença](/como-funciona/)**.

![Formulário "Emitir licença manualmente" com a escolha "Segue uma lista de acesso" / "Produtos específicos", e uma linha de licença cobrindo V3RLGPD, V3RHelp! e mais 1, com ativações listadas por produto](/assets/screenshots/licencas-emitir-lista-acesso.png)

![Lista de licenças mostrando a coluna Cobertura (produtos cobertos e a lista de acesso seguida, quando houver) e a coluna Ativações detalhada por produto](/assets/screenshots/licencas-cobertura.png)

![Cartões de estatística no topo da tela: total de licenças, ativas, suspensas por falta de pagamento e revogadas](/assets/screenshots/licencas-cards-status.png)

![Lista de licenças mostrando os cinco status lado a lado: Ativa, Revogada, Expirada, Suspensa por falta de pagamento e Em carência](/assets/screenshots/licencas-status-novos.png)

Uma licença cobre **um ou mais produtos** — desde a licença de um cliente comum, que continua cobrindo um produto só, até a licença de uma parceria que segue uma lista de acesso e cobre todo o catálogo. Veja **[Emitir uma licença](/processos/emitir-licenca/)** para a diferença entre seguir uma lista e marcar produtos específicos.

## Colunas da listagem

| Coluna | O que mostra |
|---|---|
| Chave | `license_key` |
| Cobertura | os produtos cobertos; se a licença segue uma lista, o nome da lista aparece abaixo dos produtos |
| Cliente | nome e e-mail |
| Status | Ativa / Em carência / Suspensa por falta de pagamento / Expirada / Revogada — veja **[Como funciona a licença](/como-funciona/)** para o que diferencia carência de suspensão |
| Ativações | usadas / máximo (ou "ilimitado") **por produto** — uma linha por produto coberto, quando são vários |
| Expira em | data, ou "sem validade" |
| Origem | rótulo cadastrado |
| Tipo | rótulo cadastrado |

## Filtros

Status, Produto (filtra licenças que cobrem aquele produto, mesmo cobrindo outros também), Cliente (nome ou e-mail).

## Campos do formulário de emissão

O que a licença cobre (Segue uma lista de acesso / Produtos específicos), Cliente, Tipo de licença, Máximo de ativações (vazio = padrão de cada produto), Origem, Anotação (opcional).

## Ações

Ver ativações · Renovar licença · Revogar licença (linha a linha e em lote). Selecionando mais de uma licença aparecem os botões **Renovar selecionadas** e **Revogar selecionadas**; a confirmação do lote avisa quando a seleção mistura tipos de licença diferentes, porque cada uma renova com o próprio vencimento (veja **[Renovar uma licença](/processos/renovar-licenca/)**).
