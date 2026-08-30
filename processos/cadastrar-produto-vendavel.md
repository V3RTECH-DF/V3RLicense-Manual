---
title: Cadastrar um produto vendável
parent: Como faço…
nav_order: 3
---

# Cadastrar um produto vendável

## Por que isto importa

Um produto vendável é o que liga um plugin já cadastrado no V3RLicense a um tipo de licença e, quando publicado, ao produto correspondente na loja WooCommerce. É esse cadastro — não o produto do V3RLicense sozinho — que faz um plugin aparecer para venda. Sem ele, o produto pode até existir na aba **Produtos**, mas ninguém compra: não há nada na loja para clicar em "Comprar".

A régua de quem é dono do quê importa na hora de editar depois: **o V3RLicense é dono do período** (a periodicidade vem sempre do tipo de licença escolhido aqui, nunca é digitada de novo do lado da loja); **a loja é dona do preço** (o V3RLicense nunca grava nem lê valor em reais).

## Antes de começar

O produto (plugin) e o tipo de licença que você vai usar precisam existir. Veja **[Registrar um plugin novo](/processos/cadastrar-produto/)** e **[Cadastrar tipo de licença e origem](/processos/cadastrar-tipo-e-origem/)**.

![Formulário "Novo produto vendável" com os campos Produto, Tipo de licença, Rótulo, Cota de ativações e a marcação "Oculto do catálogo"](/assets/screenshots/produtos-vendaveis-formulario.png)

## Passo a passo

1. Abra a aba **Produtos vendáveis**.
2. No formulário **Novo produto vendável**, preencha:
   - **Produto** — o plugin do V3RLicense que está sendo vendido.
   - **Tipo de licença** — define a periodicidade. Escolher um tipo **perpétuo** ("Vitalícia") gera na loja um produto **avulso**, cobrado uma vez; qualquer outro tipo (mensal, trimestral, anual…) gera uma **assinatura**, cobrada de novo a cada ciclo.
   - **Rótulo** — o nome que aparece na loja. Não precisa repetir o nome do plugin sozinho; "V3RHelp! — Assinatura anual" orienta o cliente melhor do que só "V3RHelp!".
   - **Cota de ativações** — deixe em branco para herdar o padrão do produto, ou preencha para este cadastro específico ter um limite diferente (útil no plano oculto/negociado, abaixo).
   - **Oculto do catálogo** — marque para um plano negociado com uma empresa específica (preço ou cota combinados à parte), que não deve aparecer na loja para o público em geral. O link direto de compra continua funcionando; só a vitrine não lista.
3. Clique em **Criar produto vendável**. O cadastro nasce **sem publicar** — ele ainda não existe na loja.
4. Na listagem, clique no ícone de nuvem (**Publicar/atualizar no WooCommerce**) da linha. Isso cria o produto na loja **em rascunho e sem preço**.
5. Vá à aba **WooCommerce → Produtos**, abra o produto recém-criado, defina o **preço** e mude o status para **Publicado**. Só a partir daqui o cliente consegue comprar.

{: .example }
> **Exemplo:** produto "V3REvent", tipo de licença "Vitalícia" → rótulo "V3REvent — Licença vitalícia" → publicado como produto avulso na loja, preço definido em R$ 890,00 pelo próprio WooCommerce.

## Dicas e armadilhas

{: .warning }
> **O cadastro nasce em rascunho e sem preço de propósito.** Não é um passo faltando — é o que evita um produto ir ao ar cobrando R$ 0,00 por descuido, porque publicar aqui só cria o registro na loja; o preço e o "ao vivo" ficam sempre a cargo do operador na tela do WooCommerce.

- **Publicar de novo ajusta o MESMO produto** — clicar em "Publicar/atualizar" numa linha já publicada não cria um segundo produto na loja; atualiza o nome e a periodicidade do que já existe (rastreado pela coluna WooCommerce, que mostra o número do produto).
- **Trocar o tipo de licença reclassifica o produto**, de avulso para assinatura ou o inverso, em vez de criar um produto novo — o mesmo produto WooCommerce muda de tipo na próxima publicação.
- **Excluir o cadastro NUNCA apaga o produto da loja.** A exclusão remove só a linha daqui — um produto já vendido, com pedidos e clientes associados, não pode sumir do catálogo por uma limpeza do lado do V3RLicense. Para tirar de fato o produto da loja, isso é feito na própria tela do WooCommerce.
- **Seleção em lote** funciona para excluir vários cadastros de uma vez (marque as caixas e use "Excluir selecionados"); a confirmação diz quantos cadastros serão excluídos e reforça que os produtos publicados continuam na loja.

![Diálogo de confirmação "Excluir produto vendável" avisando que só o cadastro é excluído — o produto já publicado no WooCommerce permanece na loja](/assets/screenshots/produtos-vendaveis-excluir.png)

## Quando dá errado

- **"O WooCommerce está desativado (ou indisponível) neste site"** — o cadastro continua funcionando normalmente (você ainda pode criar, editar e excluir), mas o botão de publicar fica bloqueado até o WooCommerce voltar.
- **"Não foi possível publicar no WooCommerce"** — normalmente um problema temporário de comunicação com a loja. Tente de novo; persistindo, confira se o WooCommerce está mesmo ativo.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel cadastra e publica produto vendável. Definir preço e status "Publicado" é feito na tela do WooCommerce, que segue as permissões próprias dele.
