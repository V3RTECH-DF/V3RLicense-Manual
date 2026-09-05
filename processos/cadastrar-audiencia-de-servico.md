---
title: Cadastrar uma audiência de serviço
parent: Como faço…
nav_order: 2.3
---

# Cadastrar uma audiência de serviço

## Por que isto importa

Antes de qualquer produto poder emitir token de acesso a um serviço da casa (V3RSigner, e o que vier depois), o **serviço em si** precisa existir no cadastro. É um passo raro — normalmente uma vez por serviço novo, não por cliente nem por venda — mas sem ele o campo "Serviço da casa" na tela de Produtos fica vazio, e nenhuma venda gera token.

## Passo a passo

1. Abra a aba **Audiências de serviço**.
2. Clique em **Nova audiência**.
3. Preencha:
   - **Identificador (slug)** — minúsculo, sem espaço, no padrão `algo` ou `algo-com-hifen`. Vira o valor gravado dentro de todo token emitido para este serviço (o `aud`, no jargão de quem verifica). Travado depois de criado.
   - **Rótulo** — o nome de exibição, usado nesta lista e nos filtros de **[Tokens de serviço](/modulos/tokens-de-servico/)**.
4. Salve. A audiência nasce **Ativa**.
5. Vá em **[Produtos](/modulos/produtos/)**, abra o produto que deve dar acesso a esse serviço, e escolha-o no campo **Serviço da casa (opcional — token de acesso)**.

## Exemplo concreto

O V3RSigner precisa que quem compra o plano "V3RSigner Profissional" receba também um token de acesso. Você cadastra a audiência com identificador `v3rsigner` e rótulo "V3RSigner", depois abre o produto correspondente e escolhe "V3RSigner" no campo de serviço. A partir da próxima venda desse produto, cada licença emitida já sai com o token.

## Dicas e armadilhas

- **O slug é para sempre.** Ele fica gravado dentro de cada token já emitido — mudar depois quebraria a verificação do lado do serviço para todo token existente. Por isso é travado na tela.
- **Cadastrar a audiência não emite nada sozinho.** O efeito só aparece quando um produto é ligado a ela (passo 5) e uma venda **nova** acontece — vendas anteriores àquela ligação não recebem token retroativamente.
- **Desativar não é excluir.** Uma audiência inativa mantém os tokens já emitidos funcionando (a revogação deles é outra decisão, feita em **[Gerenciar tokens de serviço](/processos/gerenciar-tokens-de-servico/)**); ela só sai da lista de opções para **novas** ligações de produto.

## Quando dá errado

**O campo "Serviço da casa" não mostra a audiência que acabei de criar** — confira se ela ficou marcada como Ativa; audiências inativas não aparecem no seletor de Produtos.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel cadastra, edita e desativa audiências de serviço.
