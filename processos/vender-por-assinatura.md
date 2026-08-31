---
title: Vender um plugin por assinatura
parent: Como faço…
nav_order: 3.4
---

# Vender um plugin por assinatura

## Por que isto importa

Um plugin vendido por assinatura tem **um produto só** na loja: você cadastra as **combinações** de duração e número de sites nesta tela, cada uma com o próprio preço, e quem compra escolhe as duas coisas na mesma página do produto — o preço acompanha a escolha. É o caminho mais comum de venda do V3RLicense.

O produto continua nascendo **em rascunho**, mesmo já tendo preço definido em cada combinação — publicar aqui não coloca nada no ar sozinho. Nada entra no catálogo por engano só porque você cadastrou uma combinação.

{: .important }
> **Isto não vale para licença perpétua nem para venda negociada com uma empresa específica.** Perpétua não é assinatura, e não cabe numa combinação de duração; venda negociada é oculta da vitrine pública, e toda combinação cadastrada aqui aparece para todo mundo. Os dois continuam pela outra seção da mesma tela — veja **[Vender uma licença perpétua ou um plano negociado](/processos/vender-perpetua-negociada/)**.

## Antes de começar

O produto (plugin) precisa existir — veja **[Registrar um plugin novo](/processos/cadastrar-produto/)**. Os tipos de licença que você vai oferecer como duração também — veja **[Cadastrar tipo de licença e origem](/processos/cadastrar-tipo-e-origem/)**; só entram aqui tipos **ativos** e **não perpétuos**. O WooCommerce Subscriptions precisa estar ativo no site para publicar (o cadastro das combinações funciona sem ele; só publicar exige).

<!-- CAPTURA PENDENTE: venda-do-plugin-assinatura-formulario.png — Tela "Venda do plugin", seção "Produto por assinatura (duração × sites)", com o formulário "Nova combinação" (Duração, Número de sites, Preço) acima da tabela já com duas ou três combinações cadastradas. Capturar a tela completa (as duas seções aparecem juntas, uma abaixo da outra). -->

## Passo a passo

1. Na aba **Produtos**, clique no ícone **Venda do plugin** da linha do plugin.
2. Na seção **Produto por assinatura (duração × sites)**, preencha o formulário **Nova combinação**:
   - **Duração** — o tipo de licença que esta opção de compra concede (mensal, trimestral, semestral, anual…).
   - **Número de sites** — quantas ativações a licença gerada por esta combinação permite. Deixe em branco para ilimitado.
   - **Preço (R$)** — o valor desta combinação específica. O preço é definido aqui, não na tela do WooCommerce.
3. Clique em **Adicionar combinação**. Repita para cada opção de duração/sites que o plugin vai oferecer.
4. Quando tiver ao menos uma combinação, clique em **Publicar/atualizar na loja**. Isso cria (ou atualiza) o produto único, com uma variação do WooCommerce para cada combinação cadastrada — em **rascunho**, mesmo já tendo preço.
5. Vá à aba **WooCommerce → Produtos**, abra o produto recém-criado e mude o status para **Publicado**. Só a partir daqui o cliente consegue comprar.
6. Publicar de novo depois de acrescentar, editar ou remover combinações **atualiza o mesmo produto** — nunca cria um segundo.

{: .example }
> **Exemplo:** produto "V3RLGPD" recebe três combinações — mensal/1 site a R$ 49,90, mensal/5 sites a R$ 149,90 e anual/5 sites a R$ 1.499,00. Depois de publicar, a página do produto na loja mostra um seletor de duração e um de número de sites; o cliente escolhe "Anual" + "5 sites" e vê R$ 1.499,00, sem precisar procurar um produto diferente para cada combinação.

## Dicas e armadilhas

{: .warning }
> **"Número de sites" em branco é ilimitado nesta seção** — não confunda com a outra seção da mesma tela (**[Licença perpétua e venda negociada](/processos/vender-perpetua-negociada/)**), onde "Ativações" em branco significa outra coisa: o padrão cadastrado no produto. O erro é silencioso — a licença sai com a cota errada, sem mensagem de aviso.

- **Duração perpétua não aparece na lista.** Se o tipo que você esperava ver não está no seletor, confira se ele está marcado como ativo e se não é o tipo perpétuo — perpétua só entra pela outra seção, em **[Vender uma licença perpétua ou um plano negociado](/processos/vender-perpetua-negociada/)**.
- **Duas combinações iguais não cabem na mesma oferta.** Mensal/5 sites já cadastrado com um preço não pode ser cadastrado de novo com outro preço — edite a combinação existente em vez de tentar duplicar.
- **Alterar o preço pelo WooCommerce direto não pega.** A próxima vez que alguém clicar em "Publicar/atualizar na loja" nesta tela, o preço volta a ser o que está cadastrado aqui — o preço é nosso, não da loja.
- **Remover uma combinação publicada tira a opção da loja na próxima publicação** — a variação correspondente também sai do WooCommerce. Cliente que já comprou aquela combinação **não perde a licença**; a remoção só impede compra nova.
- **Trocar o preço de uma combinação não muda o de quem já assina.** WooCommerce Subscriptions mantém o valor da assinatura ativa no que era no momento da compra; o preço novo vale só para quem assinar dali para a frente.

## Quando dá errado

- **Botão "Publicar/atualizar na loja" desabilitado** — confira, na ordem: se há ao menos uma combinação cadastrada, se o WooCommerce está ativo, e se o WooCommerce Subscriptions está ativo. Falta qualquer um dos três e o botão fica bloqueado, com o aviso correspondente na própria tela.
- **"Não foi possível salvar a combinação"** — normalmente uma duração já usada com o mesmo número de sites, ou um preço inválido (vazio, negativo, ou não numérico) — preço é obrigatório nesta seção. Confira a combinação e o preço antes de tentar de novo.
- **"Não foi possível publicar no WooCommerce"** — em geral um problema temporário de comunicação com a loja. Tente de novo; persistindo, confira se o WooCommerce e o WooCommerce Subscriptions estão mesmo ativos.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel cadastra e publica combinações. O status final de "Publicado" e o momento de deixar a loja realmente ao vivo continuam sendo decisão de quem opera a loja, na própria tela do WooCommerce.
