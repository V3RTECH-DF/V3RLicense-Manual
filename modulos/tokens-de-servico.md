---
title: Tokens de serviço
parent: Telas do painel
nav_order: 9.7
---

# Tokens de serviço

Veja o passo a passo em **[Gerenciar tokens de serviço](/processos/gerenciar-tokens-de-servico/)**.

![Lista de tokens de acesso a serviço, com filtros por audiência, situação e trava, os totais por trava no topo e a coluna de ações com o ícone de revogar](/assets/screenshots/tokens-de-servico-lista.png)

Esta é a listagem de todo **token de acesso a serviço da casa** já emitido — o mesmo conceito descrito em **[Token de acesso a serviço da casa](/como-funciona/#token-de-acesso-a-serviço-da-casa)**, aqui do lado do operador. Não confunda com **[Tokens de publicação](/modulos/tokens-de-publicacao/)**: aquele é credencial de máquina para publicar release; este é o que o **cliente** usa para consumir um serviço.

{: .important }
> **Você nunca vê o valor do token aqui — só os metadados.** A cadeia em claro só existe na conta do próprio cliente, na aba "Minhas licenças". É deliberado: o painel não é o lugar de guardar segredo de cliente, e essa separação é o que impede o operador de virar o cartório de senhas de todo mundo. Se o cliente perdeu o valor, ele mesmo copia de novo na própria conta — não existe "reenviar token" para o suporte fazer.

## Totais por trava

Três números, no topo da tela: quantos tokens ativos estão **sem trava**, quantos têm **certificado** e quantos têm **organização** (esta última reservada para uso futuro — nenhum token nasce com ela hoje). O total de "sem trava" é o que merece atenção: é o conjunto mais exposto a vazamento, porque qualquer um com a cadeia consegue usar.

## Filtros

**Audiência** (qual serviço) · **Situação** (Ativos/Revogados) · **Trava** (Sem trava/Certificado/Organização).

## Colunas da listagem

Identificador do token (`jti`) · Audiência · Trava · Situação (com o motivo, quando revogado) · Ações.

## Revogar — individual e em lote

Cada linha ativa tem um ícone de **Revogar**. Selecionando mais de uma linha (checkbox de cada linha, ou "selecionar todos os tokens ativos"), aparece o botão **Revogar selecionados (N)** — a confirmação sempre mostra quantos tokens serão afetados antes de executar, nunca uma revogação silenciosa.

Um campo opcional, **Motivo da próxima revogação**, fica disponível antes de confirmar — preenchido ou não, ele só documenta o motivo (aparece depois na coluna Situação); não muda o efeito da revogação.

{: .warning }
> **Revogar aqui tem o mesmo atraso de propagação de sempre — até 1 hora.** Veja **[Token de acesso a serviço da casa](/como-funciona/#token-de-acesso-a-serviço-da-casa)** para o porquê. Revogar pelo painel não é mais rápido do que o cliente revogar pela própria conta; use quando for você, e não o cliente, quem precisa agir — por exemplo, suspeita de fraude ou pedido formal de cancelamento.
