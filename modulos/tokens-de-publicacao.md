---
title: Tokens de publicação
parent: Telas do painel
nav_order: 7
---

# Tokens de publicação

Veja o passo a passo em **[Gerenciar tokens de publicação](/processos/gerenciar-tokens-publicacao/)**.

![Lista de tokens de publicação: "GitHub Action - V3RLGPD" e "GitHub Action - V3REvent", ambos com status Ativo, data de criação e último uso](/assets/screenshots/tokens-lista.png)

{: .note }
> Este print é anterior à coluna **Escopo** (produto que o token publica) — a lista real hoje mostra também essa coluna, com um selo de alerta quando o token está com o escopo mais permissivo ("Todos os produtos"). Recaptura pendente.

O modal que aparece logo depois de gerar um token não tem captura aqui — gerar um de verdade só para o print criaria um token descartável em produção. O que ele mostra: o valor do token em claro, um aviso de que **este é o único momento em que ele aparece**, o botão **Copiar token** e o botão **Já copiei, fechar**. Veja o passo a passo completo em **[Gerenciar tokens de publicação](/processos/gerenciar-tokens-publicacao/)**.

## Colunas da listagem

Rótulo · **Escopo** (produto que o token publica, ou "Todos os produtos") · Status (Ativo/Revogado) · Criado em · Último uso.

## Campos do formulário

Rótulo (para identificar o uso) e **Produto que este token publica** (obrigatório — é o que define o escopo, não o rótulo).

## Ações

Revogar token (só em tokens ativos; a linha não é excluída) · mudar o escopo de um token existente.

{: .warning }
> O escopo "Todos os produtos" continua existindo — é o padrão herdado de todo token emitido antes de o escopo por produto existir, e também pode ser escolhido de propósito ao reatribuir um token. Detalhe completo em **[Gerenciar tokens de publicação](/processos/gerenciar-tokens-publicacao/)**.
