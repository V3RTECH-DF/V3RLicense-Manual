---
title: Gerenciar tokens de serviço
parent: Como faço…
nav_order: 2.6
---

# Gerenciar tokens de serviço

## Por que isto importa

O cliente configura a trava, reemite e revoga o próprio token de acesso a serviço pela conta dele (veja **[Token de acesso a serviço da casa](/como-funciona/#token-de-acesso-a-serviço-da-casa)**) — na maior parte dos casos, você nunca precisa tocar nisto. Esta tela existe para quando é **você** quem precisa agir: suspeita de fraude, pedido formal de cancelamento, ou uma auditoria de quantos tokens estão circulando sem trava.

## Passo a passo — consultar e filtrar

1. Abra a aba **Tokens de serviço**.
2. Use os filtros **Audiência**, **Situação** e **Trava** para reduzir a lista.
3. Os três totais no topo (**Sem trava**, **Certificado**, **Organização**) mostram quantos tokens ativos existem em cada trava, já considerando os filtros aplicados.

## Passo a passo — revogar um token

1. Localize a linha do token.
2. Clique no ícone **Revogar**.
3. Se quiser, preencha o **Motivo** (ex.: "fraude", "pedido do cliente") — fica registrado na coluna Situação.
4. Confirme.

## Passo a passo — revogar em lote

1. Marque o checkbox de cada token a revogar, ou **Selecionar todos os tokens ativos** para marcar a página inteira.
2. Clique em **Revogar selecionados (N)** — o número mostra quantos serão afetados.
3. Preencha o motivo, se quiser, e confirme.

{: .example }
> **Exemplo:** um cliente relata que o certificado configurado no token foi comprometido e pede para cancelar o acesso imediatamente enquanto ele providencia um certificado novo. Filtre por **Audiência** = V3RSigner e localize o token dele pela lista (ou peça o identificador a ele); revogue com o motivo "certificado comprometido, a pedido do cliente". Avise-o de que o token antigo deixa de valer em até 1 hora e que ele mesmo emite um novo, com o certificado novo, assim que estiver pronto.

## Dicas e armadilhas

- **Revogar aqui produz o mesmo efeito, e a mesma janela de propagação, que o cliente revogando pela própria conta.** Não é um caminho "mais rápido" — é o caminho para quando é você, e não ele, quem precisa iniciar.
- **Você nunca vê o valor do token** — nem para conferir, nem para repassar ao cliente. Se ele perdeu o valor, ele mesmo copia de novo na própria conta; não existe reenvio pelo suporte.
- **Muitos tokens sem trava não é, por si só, um problema a corrigir por você** — a trava é decisão do cliente. Mas é um bom indicador de quem vale a pena orientar a configurar certificado, principalmente se o volume chamar atenção.

## Quando dá errado

**Revoguei um token, mas o cliente diz que ainda funciona** — dentro da primeira hora, isso é esperado (veja o porquê em **[Token de acesso a serviço da casa](/como-funciona/#reemitir-e-revogar--e-por-que-não-é-instantâneo)**). Passada a hora e o problema persistir, confira se revogou o token certo — um cliente pode ter mais de uma licença, cada uma com o próprio token.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel filtra e revoga. Configurar a trava (informar certificado) só o cliente faz, pela própria conta — não existe essa ação aqui.
