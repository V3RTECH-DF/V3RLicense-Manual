---
title: Vender uma licença perpétua ou um plano negociado
parent: Como faço…
nav_order: 3.6
---

# Vender uma licença perpétua ou um plano negociado

## Por que isto importa

Esta seção da tela **Venda do plugin** liga um plugin já cadastrado a um tipo de licença e, quando publicado, ao produto correspondente na loja WooCommerce. É esse cadastro — não o produto do V3RLicense sozinho — que faz um plugin aparecer para venda. Sem ele, o produto pode até existir na aba **Produtos**, mas ninguém compra: não há nada na loja para clicar em "Comprar".

Use este caminho para dois casos que não cabem em **[Vender um plugin por assinatura](/processos/vender-por-assinatura/)**: licença **perpétua** (não é assinatura, e não cabe numa combinação de duração) e **venda negociada** com uma empresa específica (preço ou cota combinados à parte, oculta da vitrine pública — toda combinação da seção de assinatura aparece para todo mundo). O tipo de licença aqui aceita **qualquer periodicidade** — inclusive um plano anual com desconto fechado para uma empresa, não só perpétua.

## Antes de começar

O produto (plugin) e o tipo de licença que você vai usar precisam existir. Veja **[Registrar um plugin novo](/processos/cadastrar-produto/)** e **[Cadastrar tipo de licença e origem](/processos/cadastrar-tipo-e-origem/)**.

<!-- CAPTURA PENDENTE: venda-do-plugin-perpetua-formulario.png — Tela "Venda do plugin", seção "Licença perpétua e venda negociada", com o formulário preenchido (Produto, Tipo de licença, Rótulo, Preço, Ativações, "Oculto do catálogo") acima da listagem já cadastrada. -->

## Passo a passo

1. Na aba **Produtos**, clique no ícone **Venda do plugin** da linha do plugin.
2. Na seção **Licença perpétua e venda negociada**, preencha:
   - **Produto** — o plugin do V3RLicense que está sendo vendido.
   - **Tipo de licença** — define a periodicidade. Escolher um tipo **perpétuo** ("Vitalícia") gera na loja um produto **avulso**, cobrado uma vez; qualquer outro tipo (mensal, trimestral, anual…) gera uma **assinatura**, cobrada de novo a cada ciclo.
   - **Rótulo** — o nome que aparece na loja. Não precisa repetir o nome do plugin sozinho; "V3RHelp! — Assinatura anual, plano ACME" orienta melhor do que só "V3RHelp!".
   - **Preço (R$)** — opcional. Se você definir um valor aqui, ele passa a ser o preço que vale na loja a partir da próxima publicação. Deixe em branco só se o preço já estiver definido na tela do WooCommerce e você não quiser que esta tela mexa nele.
   - **Ativações** — deixe em branco para herdar o padrão do produto (se o produto também não tiver padrão, fica sem limite), ou preencha para este cadastro específico ter um limite diferente — útil na venda negociada.
   - **Oculto do catálogo** — marque para uma venda negociada com uma empresa específica, que não deve aparecer na loja para o público em geral. O link direto de compra continua funcionando; só a vitrine não lista.
3. Clique em **Criar**. O cadastro nasce **sem publicar** — ele ainda não existe na loja.
4. Na listagem, clique no ícone de nuvem (**Publicar/atualizar no WooCommerce**) da linha. Isso cria o produto na loja **em rascunho**, com o preço que você definiu no passo 2 (se definiu).
5. Vá à aba **WooCommerce → Produtos**, abra o produto recém-criado e mude o status para **Publicado** — confirmando o preço, se você deixou o campo em branco no passo 2. Só a partir daqui o cliente consegue comprar.

{: .example }
> **Exemplo 1 (perpétua):** produto "V3REvent", tipo de licença "Vitalícia", preço R$ 890,00 preenchido aqui → publicado como produto avulso na loja, já com o preço certo, faltando só mudar para "Publicado".
>
> **Exemplo 2 (negociada):** produto "V3RHelp!", tipo "Anual", rótulo "V3RHelp! — Plano ACME", preço R$ 3.200,00, "Oculto do catálogo" marcado → produto anual com desconto fechado para a empresa ACME, fora da vitrine pública, acessível só pelo link direto de compra.

## Dicas e armadilhas

{: .warning }
> **"Ativações" em branco não é ilimitado aqui** — é o padrão cadastrado no produto. Só fica sem limite se o produto **também** não tiver padrão definido. Não confunda com a outra seção da mesma tela (**[Vender um plugin por assinatura](/processos/vender-por-assinatura/)**), onde "Número de sites" em branco é sempre ilimitado. O erro é silencioso: a licença sai com a cota errada, sem aviso nenhum.

- **O preço passou a ser nosso.** Desde a v0.21.0, quem alterar o valor direto pelo WooCommerce vê a alteração ser **sobrescrita** na próxima vez que alguém publicar a partir desta tela. Se você quer que o WooCommerce continue mandando no preço deste cadastro, deixe o campo **Preço** em branco aqui — publicar assim não mexe no que já está na loja.
- **Publicar de novo ajusta o MESMO produto** — clicar em "Publicar/atualizar" numa linha já publicada não cria um segundo produto na loja; atualiza o nome, a periodicidade e o preço (se definido) do que já existe, rastreado pela coluna WooCommerce, que mostra o número do produto.
- **Trocar o tipo de licença reclassifica o produto**, de avulso para assinatura ou o inverso, em vez de criar um produto novo — o mesmo produto WooCommerce muda de tipo na próxima publicação.
- **Excluir o cadastro NUNCA apaga o produto da loja.** A exclusão remove só a linha daqui — um produto já vendido, com pedidos e clientes associados, não pode sumir do catálogo por uma limpeza do lado do V3RLicense. Para tirar de fato o produto da loja, isso é feito na própria tela do WooCommerce.
- **Seleção em lote** funciona para excluir vários cadastros de uma vez (marque as caixas e use "Excluir selecionados"); a confirmação diz quantos cadastros serão excluídos e reforça que os produtos publicados continuam na loja.

## Quando dá errado

- **"O WooCommerce está desativado (ou indisponível) neste site"** — o cadastro continua funcionando normalmente (você ainda pode criar, editar e excluir), mas o botão de publicar fica bloqueado até o WooCommerce voltar.
- **"Não foi possível publicar no WooCommerce"** — normalmente um problema temporário de comunicação com a loja. Tente de novo; persistindo, confira se o WooCommerce está mesmo ativo.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel cadastra e publica esta seção. Definir o status "Publicado" — e confirmar o preço, se você deixou o campo em branco no cadastro — é feito na tela do WooCommerce, que segue as permissões próprias dele.
