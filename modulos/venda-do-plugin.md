---
title: Venda do plugin
parent: Telas do painel
nav_order: 3.5
---

# Venda do plugin

Veja o passo a passo em **[Vender um plugin por assinatura](/processos/vender-por-assinatura/)** e em **[Vender uma licença perpétua ou um plano negociado](/processos/vender-perpetua-negociada/)**.

Acessada pelo ícone **Venda do plugin** (uma loja) na linha do plugin, na listagem de **[Produtos](/modulos/produtos/)**. É uma tela só, com duas seções — não duas telas separadas.

{: .important }
> **Um campo em branco significa coisas opostas nas duas seções.** Em **Produto por assinatura**, "Número de sites" em branco é **ilimitado**. Em **Licença perpétua e venda negociada**, "Ativações" em branco é **o padrão cadastrado no produto** — e só fica sem limite se o produto também não tiver padrão. A própria tela mostra o número real do produto ao lado do campo; confira antes de salvar.

## Seção "Produto por assinatura (duração × sites)"

O caso mais comum: você monta combinações de duração (tipo de licença) e número de sites, cada uma com o próprio preço, e elas viram **um único produto na loja** — quem compra escolhe as duas coisas na mesma página do produto.

### Campos da combinação

Duração (tipo de licença — só aparecem tipos ativos e não perpétuos) · Número de sites (em branco = ilimitado) · Preço (R$), obrigatório.

### Colunas da tabela de combinações

Duração · Sites · Preço · WooCommerce (número da variação publicada, ou "Não publicado") · Ações.

### Ações

**Publicar/atualizar na loja** — cria o produto único na primeira vez (uma variação por combinação) ou atualiza o mesmo produto nas vezes seguintes. Exige WooCommerce Subscriptions ativo e ao menos uma combinação cadastrada.

**Editar combinação** · **Remover da venda** — remover uma combinação já publicada também remove a variação correspondente no WooCommerce.

## Seção "Licença perpétua e venda negociada"

Os dois casos que não cabem em assinatura: a **perpétua** (vitalícia, sem renovação) e a **venda negociada** diretamente com uma empresa, oculta do catálogo público. Aceita **qualquer periodicidade** — inclusive um plano anual com condição especial fechada com uma empresa, não só perpétua.

### Campos do formulário

Produto · Tipo de licença (define a periodicidade; qualquer tipo, incluindo perpétuo) · Rótulo (nome exibido na loja) · Preço (R$), opcional · Ativações (vazio = padrão do produto) · Oculto do catálogo (venda negociada com uma empresa, sem aparecer na vitrine pública).

### Colunas da listagem

Rótulo · Produto · Tipo de licença · Catálogo (Visível / Oculto — negociado) · WooCommerce (Ainda não publicado / Rascunho / Publicado / Pendente / Privado / Na lixeira, com o número do produto) · Ações.

### Ações

**Publicar/atualizar no WooCommerce** — cria o produto na primeira vez, em rascunho; nas vezes seguintes, atualiza o mesmo produto. Fica desabilitado quando o WooCommerce está indisponível.

**Editar** · **Excluir cadastro** — excluir aqui remove só o cadastro; o produto já publicado na loja (se houver) permanece intacto.

## O preço passou a ser nosso

Nas duas seções, o preço definido aqui é o que vale: quem alterar o valor direto pelo WooCommerce vê a alteração ser **sobrescrita** na próxima vez que alguém publicar a partir desta tela. A única exceção é o cadastro antigo que nunca teve preço definido aqui — o campo aparece vazio, e publicar assim **não apaga** o preço que já estiver na loja.

{: .note }
> **Sem produto na loja ainda? A causa é dupla.** "Ainda não publicado" (ou "Não publicado") significa que ninguém clicou em publicar. Um produto que já foi publicado mas mostra "Rascunho" precisa de mais um passo: alguém, na própria tela do WooCommerce, confere o preço e muda o status para "Publicado".
