---
title: Configurações
parent: Telas do painel
nav_order: 11
---

# Configurações

![Tela de Configurações com a seção "Aviso ao operador" e o campo E-mail do operador preenchido com suporte@v3rtech.com.br](/assets/screenshots/configuracoes-email-operador.png)

Tela de configuração geral do plugin — nasce pequena, só com o endereço que recebe o aviso de vencimento das licenças **concedidas** (isenções). É aqui que as próximas configurações do V3RLicense vão morar conforme o produto crescer.

## Por que isto importa

Licença comprada avisa o **cliente** por e-mail quando está perto de vencer (veja **[Como funciona a licença](/como-funciona/)**). Licença **concedida** (isenção, cortesia) segue outra regra: o cliente dela nunca recebe e-mail — quem é avisado é **o operador**, porque a renovação dessas licenças é sempre manual, feita por quem opera o V3RLicense.

## Campos

**E-mail do operador** — o endereço que recebe esse aviso. Vem preconfigurado com `suporte@v3rtech.com.br`; troque se o time responsável por renovar isenções mudar.

**Página com os produtos disponíveis** (desde a v0.16.0) — uma página do site, escolhida aqui pelo gestor. Ela é usada na aba **"Minhas licenças"** do cliente (veja **[Como funciona a licença](/como-funciona/)**) quando o produto original de uma licença **saiu de venda ou foi despublicado**: em vez de virar um link quebrado, a aba explica que aquele produto não está mais disponível para contratação e oferece essa página, mais o contato.

## Por que isto importa

Licença comprada avisa o **cliente** por e-mail quando está perto de vencer (veja **[Como funciona a licença](/como-funciona/)**). Licença **concedida** (isenção, cortesia) segue outra regra: o cliente dela nunca recebe e-mail — quem é avisado é **o operador**, porque a renovação dessas licenças é sempre manual, feita por quem opera o V3RLicense.

## Passo a passo

1. Abra a aba **Configurações**.
2. Preencha **E-mail do operador**.
3. Se quiser, escolha a **Página com os produtos disponíveis**.
4. Clique em **Salvar**.

## Dicas e armadilhas

{: .tip }
> **Use a [renovação em lote](/processos/renovar-licenca/) para agir sobre o aviso.** O e-mail que chega aqui já sugere isso — regularizar todas as licenças concedidas vencendo de uma vez, em vez de uma por uma.

- **Deixar o campo de e-mail com um endereço que ninguém lê é a forma mais comum de perder o prazo de uma isenção sem perceber** — o aviso sai certinho, só que para a caixa errada.
- **Deixar a página de produtos disponíveis vazia não quebra nada** — o cliente cuja licença cobre um produto descontinuado ainda vê o contato. Mas é oportunidade perdida: quem estava disposto a pagar de novo não recebe nenhuma alternativa, só um e-mail para escrever.
