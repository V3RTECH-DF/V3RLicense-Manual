---
title: Remover um release publicado
parent: Como faço…
nav_order: 11
---

# Remover um release publicado

## Por que isto importa

Às vezes um release sai com defeito e precisa ser retirado antes de mais clientes atualizarem para ele. Remover apaga o arquivo do disco e invalida qualquer link de download já gerado para essa versão — é uma ação que afeta quem já baixou ou está prestes a baixar.

## Passo a passo

**Um release:**
1. Abra a aba **Releases** e selecione o produto.
2. Clique no ícone **Remover release** na linha da versão.
3. Leia o aviso — ele muda dependendo se é a versão mais recente ou não — e confirme.

**Vários de uma vez:** marque as caixas e use a ação em lote equivalente; o diálogo avisa se a seleção inclui a versão mais recente de algum produto.

## Exemplo

A versão `1.24.0` do V3REvent foi publicada com um changelog que promete uma correção que na verdade não entrou no build (erro de pipeline). Antes que mais clientes atualizem para ela, você remove o release `1.24.0` — o site volta a oferecer `1.23.x` (a versão anterior) como a mais recente disponível, até uma `1.24.1` correta ser publicada.

## Dicas e armadilhas

{: .important }
> **Removendo a versão mais recente, o aviso é mais forte de propósito:** "removê-la muda o que os clientes recebem no próximo update-check." Isso significa que quem ainda não atualizou passa a ver a versão anterior como a mais nova disponível — o efeito é imediato e afeta todo cliente com licença ativa daquele produto, não só quem já baixou.

- **O arquivo é apagado do disco** — não é uma marca de "oculto", é remoção de verdade. Se for reaproveitar o mesmo número de versão depois, será preciso publicar de novo com o zip correto.
- **Qualquer link de download já gerado para essa versão para de funcionar** — se alguém copiou um link direto antes da remoção, ele passa a falhar.

## Quando dá errado

Não há uma mensagem de erro específica aqui além de falha de permissão ou de rede — se a remoção não refletir na lista, recarregue a aba para confirmar antes de tentar de novo (evita remover duas vezes por engano, o que não causa dano, mas confunde).

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel remove release de qualquer produto. Justamente por afetar quem já está usando o release, confirme antes de clicar — principalmente quando o aviso disser que é a versão mais recente.
