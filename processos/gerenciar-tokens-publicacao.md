---
title: Gerenciar tokens de publicação
parent: Como faço…
nav_order: 9
---

# Gerenciar tokens de publicação

## Por que isto importa

Um token de publicação é uma credencial de máquina — normalmente para uma pipeline de CI (GitHub Action) publicar release automaticamente, sem uma pessoa entrar no painel. Ele tem escopo restrito: **só publica release**, nunca emite licença, revoga ou lê dado de cliente.

{: .important }
> **O token vale para um produto só.** Ao gerar um token você escolhe o **produto** que ele autoriza publicar — é obrigatório, não um rótulo decorativo. Um token gerado para o V3REvent não publica release do V3RLGPD, mesmo que as duas credenciais estejam válidas ao mesmo tempo. Um token vazado publica release de um produto só, nunca dos sete.

## Passo a passo — gerar

1. Abra a aba **Tokens de publicação**.
2. Preencha **Rótulo** com algo que identifique o uso (ex.: "GitHub Action — v3rlgpd").
3. Selecione o **Produto que este token publica** — obrigatório.
4. Clique em **Gerar token**.
5. Um modal mostra o valor em claro **uma única vez**. Copie com o botão **Copiar token** e cole imediatamente no lugar certo (segredo da pipeline de CI, gerenciador de segredos).
6. Clique em **Já copiei, fechar**.

## Passo a passo — revogar

1. Na lista de tokens, clique no ícone **Revogar token** na linha correspondente.
2. Confirme — o token para de funcionar imediatamente.

## Passo a passo — mudar o escopo de um token existente

1. Na lista de tokens, abra o ícone de **escopo** na linha correspondente.
2. Escolha o produto, ou **Todos os produtos** para o escopo mais permissivo.
3. Salve. O valor do token não muda — só o produto que ele autoriza publicar.

{: .warning }
> **"Todos os produtos" existe, e é o escopo mais permissivo que dá para atribuir.** Ele é o padrão herdado de todo token emitido antes de o escopo por produto existir — nunca vira "não configurado". Não escolha esse escopo para um token novo só por comodidade: um token largo demais publica em nome de qualquer produto cadastrado, inclusive um que a pipeline em questão não deveria tocar.

{: .example }
> **Exemplo:** ao configurar a pipeline de release do V3RLGPD, gere um token com rótulo "GitHub Action — v3rlgpd", copie o valor e cole no secret `V3RLICENSE_PUBLISH_TOKEN` do repositório. Se a pipeline for descontinuada ou o repositório mudar de dono, revogue o token antigo e gere um novo — não reaproveite.

## Dicas e armadilhas

{: .important }
> **O valor não é recuperável.** "Este valor aparece só uma vez. Se você perder, não é possível recuperá-lo depois — só gerar um token novo." O servidor guarda apenas um hash do token, nunca o valor em claro — mesmo um administrador do banco de dados não consegue recuperar o valor original. Se perder, revogue o antigo (se ainda existir) e gere outro.
- **Revogar não apaga a linha** — ela continua na lista, marcada como revogada, para manter o histórico de quem publicou o quê.
- **Rótulo é só identificação para você** — quem limita o que o token pode fazer é o campo Produto, não o rótulo.

## Quando dá errado

- **Pipeline de CI recebe erro de autenticação ao publicar** — o token pode ter sido revogado, ou foi colado errado (com espaço, ou truncado) no segredo da pipeline. Gere um novo e atualize o segredo.
- **Publicação recusada mesmo com o token válido** — confira se o escopo do token é o produto certo. Um token do V3REvent não publica release do V3RLGPD; veja "mudar o escopo" acima se precisar reatribuir.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel gera, revoga e reatribui o escopo de qualquer token.
