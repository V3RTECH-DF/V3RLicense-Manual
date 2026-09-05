---
title: Gerenciar tokens de serviço
parent: Como faço…
nav_order: 2.6
---

# Gerenciar tokens de serviço

## Por que isto importa

O cliente configura a trava, reemite e revoga o próprio token de acesso a serviço pela conta dele (veja **[Token de acesso a serviço da casa](/como-funciona/#token-de-acesso-a-serviço-da-casa)**) — na maior parte dos casos, você nunca precisa tocar nisto. Você entra em campo em três situações: precisa **dar** acesso a alguém fora do fluxo de venda, suspeita de fraude ou recebe um pedido formal de cancelamento, ou quer **auditar** quantos tokens estão circulando sem trava.

{: .note }
> Desde a v0.33.0, não existe mais uma tela própria de "Tokens de serviço" — tudo isto acontece em **[Licenças e acessos](/modulos/licencas/)**, na linha do acesso.

## Passo a passo — emitir um token para um acesso que ainda não tem

1. Abra **Licenças e acessos** e localize o acesso (filtre por Categoria = Só acessos).
2. Se a coluna "Token de acesso" mostrar **"Não emitido"**, clique no ícone **Emitir token de acesso**, na linha dele.
3. Confirme. O token é emitido na hora, com trava "Sem trava" — o cliente configura a trava por certificado depois, na própria conta.

{: .important }
> **Emitir aqui não depende de venda.** Desde a v0.32.0, um acesso pode ganhar o token pelo painel a qualquer momento — útil para licença concedida por parceria, ou para um acesso emitido antes de o produto ganhar audiência de serviço.

## Passo a passo — revogar o token de um acesso

1. Localize a linha do acesso.
2. Clique no ícone **Revogar token de acesso**.
3. Confirme — a descrição do diálogo já avisa que o consumidor do serviço para de aceitar o token em até 1 hora, não na hora.

## Passo a passo — revogar em lote

1. Marque o checkbox de cada linha de acesso cujo token você quer revogar (a mesma seleção que serve para renovar/revogar licença em lote).
2. Com ao menos um acesso com token marcado, aparece o botão **Revogar tokens selecionados (N)**.
3. Confirme — o número no botão já mostra quantos serão afetados.

{: .example }
> **Exemplo:** um cliente relata que o certificado configurado no token foi comprometido e pede para cancelar o acesso imediatamente enquanto ele providencia um certificado novo. Filtre por Cliente (nome ou e-mail) em **Licenças e acessos**, localize a linha do acesso dele e clique em **Revogar token de acesso**. Avise-o de que o token antigo deixa de valer em até 1 hora e que ele mesmo emite um novo, com o certificado novo, assim que estiver pronto — pela própria conta, ou por você, com **Emitir token de acesso** na mesma linha.

## Dicas e armadilhas

- **Revogar aqui produz o mesmo efeito, e a mesma janela de propagação, que o cliente revogando pela própria conta.** Não é um caminho "mais rápido" — é o caminho para quando é você, e não ele, quem precisa iniciar.
- **Você nunca vê o valor do token** — nem para conferir, nem para repassar ao cliente. A coluna "Token de acesso" mostra só a trava e a validade. Se o cliente perdeu o valor, ele mesmo copia de novo na própria conta; não existe reenvio pelo suporte.
- **Nunca existem dois tokens vigentes ao mesmo tempo para o mesmo acesso.** Se já existe um vigente, o ícone da linha é **Revogar**, não **Emitir** — para trocar, revogue e emita de novo (ou oriente o cliente a **Reemitir**, que faz as duas coisas numa ação só, pela própria conta).
- **Muitos tokens sem trava não é, por si só, um problema a corrigir por você** — a trava é decisão do cliente. Mas os indicadores no topo de **Licenças e acessos** são um bom termômetro de quem vale a pena orientar a configurar certificado, principalmente se o volume chamar atenção.

## Quando dá errado

**Revoguei um token, mas o cliente diz que ainda funciona** — dentro da primeira hora, isso é esperado (veja o porquê em **[Token de acesso a serviço da casa](/como-funciona/#reemitir-e-revogar--e-por-que-não-é-instantâneo)**). Passada a hora e o problema persistir, confira se revogou o token certo — um cliente pode ter mais de um acesso, cada um com o próprio token.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel emite e revoga token de acesso. Configurar a trava (informar certificado) só o cliente faz, pela própria conta — não existe essa ação aqui.
