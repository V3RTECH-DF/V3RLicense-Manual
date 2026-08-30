---
title: Produtos vendáveis
parent: Telas do painel
nav_order: 10
---

# Produtos vendáveis

Veja o passo a passo em **[Cadastrar um produto vendável](/processos/cadastrar-produto-vendavel/)**.

{: .note }
> **Desde a v0.19.0, esta tela é só para dois casos:** licença **perpétua** (avulsa, sem periodicidade) e plano **negociado** com uma empresa específica (oculto da vitrine pública). Para um plugin vendido por assinatura no plano comum — mensal, trimestral, anual, com opção de número de sites —, use **[Oferta na loja](/modulos/oferta-na-loja/)**, que cadastra tudo num produto único.

![Listagem de produtos vendáveis com três linhas: V3REvent em licença vitalícia publicado como rascunho no WooCommerce, V3RHelp! em assinatura anual ainda não publicado, e V3RLGPD num plano mensal oculto do catálogo](/assets/screenshots/produtos-vendaveis-lista.png)

Um produto vendável liga um produto do V3RLicense (o plugin) a um tipo de licença e, depois de publicado, ao produto correspondente no WooCommerce. **O V3RLicense é dono do período** (a periodicidade do produto na loja vem do tipo de licença escolhido aqui); **a loja é dona do preço** (nunca gravado neste cadastro).

## Colunas da listagem

Rótulo · Produto · Tipo de licença · Catálogo (Visível / Oculto — negociado) · WooCommerce (Ainda não publicado / Rascunho / Publicado / Pendente / Privado / Na lixeira, com o número do produto) · Ações.

A coluna **WooCommerce** mostra o `post_status` real do produto na loja, nunca em inglês — "Rascunho" é o estado em que todo produto novo nasce, antes de o operador definir preço e publicar de fato.

## Campos do formulário

Produto · Tipo de licença (trava a periodicidade — perpétuo vira produto avulso, qualquer outro tipo vira assinatura) · Rótulo (nome exibido na loja) · Cota de ativações (vazio = padrão do produto) · Oculto do catálogo (plano negociado, sem aparecer na vitrine pública).

## Ações

**Publicar/atualizar no WooCommerce** (ícone de nuvem) — cria o produto na loja na primeira vez, em rascunho e sem preço; nas vezes seguintes, atualiza o mesmo produto. Fica desabilitado quando o WooCommerce está indisponível.

**Editar** · **Excluir cadastro** — excluir aqui remove só o cadastro; o produto já publicado na loja (se houver) permanece intacto.

{: .note }
> **Sem produto na loja ainda? A causa é dupla.** "Ainda não publicado" na coluna WooCommerce significa que ninguém clicou em publicar. Um produto que já foi publicado mas mostra "Rascunho" precisa de mais um passo: alguém define o preço e muda o status para "Publicado" na própria tela do WooCommerce.
