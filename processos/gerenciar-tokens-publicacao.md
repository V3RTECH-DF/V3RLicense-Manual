---
title: Gerenciar tokens de publicação
parent: Como faço…
nav_order: 9
---

# Gerenciar tokens de publicação

## Por que isto importa

Um token de publicação é uma credencial de máquina — normalmente para uma pipeline de CI (GitHub Action) publicar release automaticamente, sem uma pessoa entrar no painel. Ele tem escopo restrito: **só publica release**, nunca emite licença, revoga ou lê dado de cliente.

{: .warning }
> **Hoje o token não tem escopo por produto.** Qualquer token válido publica release de **qualquer** produto cadastrado, mesmo que o rótulo do token sugira que ele é "só do V3REvent" ou "só do V3RLGPD". Isso está registrado como comportamento a corrigir — até lá, trate cada token como capaz de publicar para qualquer produto, e não distribua um token para fora da equipe achando que ele está contido a um plugin.

## Passo a passo — gerar

1. Abra a aba **Tokens de publicação**.
2. Preencha **Rótulo** com algo que identifique o uso (ex.: "GitHub Action — v3rlgpd").
3. Clique em **Gerar token**.
4. Um modal mostra o valor em claro **uma única vez**. Copie com o botão **Copiar token** e cole imediatamente no lugar certo (segredo da pipeline de CI, gerenciador de segredos).
5. Clique em **Já copiei, fechar**.

## Passo a passo — revogar

1. Na lista de tokens, clique no ícone **Revogar token** na linha correspondente.
2. Confirme — o token para de funcionar imediatamente.

{: .example }
> **Exemplo:** ao configurar a pipeline de release do V3RLGPD, gere um token com rótulo "GitHub Action — v3rlgpd", copie o valor e cole no secret `V3RLICENSE_PUBLISH_TOKEN` do repositório. Se a pipeline for descontinuada ou o repositório mudar de dono, revogue o token antigo e gere um novo — não reaproveite.

## Dicas e armadilhas

{: .important }
> **O valor não é recuperável.** "Este valor aparece só uma vez. Se você perder, não é possível recuperá-lo depois — só gerar um token novo." O servidor guarda apenas um hash do token, nunca o valor em claro — mesmo um administrador do banco de dados não consegue recuperar o valor original. Se perder, revogue o antigo (se ainda existir) e gere outro.
- **Revogar não apaga a linha** — ela continua na lista, marcada como revogada, para manter o histórico de quem publicou o quê.
- **Rótulo é só identificação para você** — não limita o que o token pode fazer (ver aviso acima sobre escopo por produto).

## Quando dá errado

- **Pipeline de CI recebe erro de autenticação ao publicar** — o token pode ter sido revogado, ou foi colado errado (com espaço, ou truncado) no segredo da pipeline. Gere um novo e atualize o segredo.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel gera e revoga token, para qualquer produto.
