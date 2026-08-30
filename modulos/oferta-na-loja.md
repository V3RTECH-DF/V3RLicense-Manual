---
title: Oferta na loja
parent: Telas do painel
nav_order: 3.5
---

# Oferta na loja

Veja o passo a passo em **[Montar a oferta de um plugin na loja](/processos/cadastrar-oferta-na-loja/)**.

<!-- CAPTURA PENDENTE: oferta-na-loja-tabela-combinacoes.png — Tela "Oferta na loja" do V3RLicense com três combinações cadastradas — mensal com 1 site, mensal com 5 sites e anual com 5 sites — cada uma com preço próprio e o número da variação publicada no WooCommerce. Capturar quando a v0.19.x estiver publicada e trocar este comentário pela imagem. -->

Desde a v0.19.0, um plugin com planos por assinatura tem **um produto só** na loja, com uma **combinação** de duração (o tipo de licença) e número de sites para cada opção de compra — cada combinação com o próprio preço. É esta tela, acessada pelo ícone **Oferta na loja** na listagem de **[Produtos](/modulos/produtos/)**, que substitui cadastrar um produto vendável por forma de venda.

{: .note }
> **Isto não substitui a tela [Produtos vendáveis](/modulos/produtos-vendaveis/).** Licença **perpétua** e plano **negociado/oculto** continuam sendo cadastrados por lá — o motivo de cada caminho existir está em **[Montar a oferta de um plugin na loja](/processos/cadastrar-oferta-na-loja/)**.

## Campos do formulário de combinação

**Duração** (o tipo de licença — só aparecem tipos ativos e não perpétuos) · **Número de sites** (em branco = ilimitado) · **Preço (R$)**.

## Colunas da tabela de combinações

Duração · Sites · Preço · WooCommerce (número da variação publicada, ou "Não publicado") · Ações.

## Ações

**Publicar/atualizar na loja** — cria o produto único na loja na primeira vez (com uma variação por combinação cadastrada) ou atualiza o mesmo produto nas vezes seguintes. Exige o WooCommerce Subscriptions ativo; fica desabilitado sem ele, sem o WooCommerce, ou sem nenhuma combinação cadastrada ainda.

**Editar combinação** · **Remover da venda** — remover uma combinação já publicada também remove a variação correspondente no WooCommerce.

{: .important }
> **Aqui não há campo de "oculto do catálogo".** Esse recurso é exclusivo do plano negociado, cadastrado em **[Produtos vendáveis](/modulos/produtos-vendaveis/)** — toda combinação desta tela aparece na vitrine pública do produto.
