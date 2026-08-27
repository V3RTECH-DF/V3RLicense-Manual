---
title: Registrar um plugin novo
parent: Como faço…
nav_order: 1
---

# Registrar um plugin novo

## Por que isto importa

O V3RLicense só emite licença e aceita release para um produto que já existe no cadastro. Antes da primeira licença ou do primeiro release de um plugin, ele precisa nascer aqui — com o **slug certo**, porque é esse mesmo texto que vai ter que bater com o nome da pasta dentro do zip na hora de publicar (veja **[Publicar uma versão](/processos/publicar-uma-versao/)**).

## Passo a passo

1. No painel do V3RLicense, abra a aba **Produtos**.
2. Clique em **Novo produto** (ou o formulário de criação, se já estiver na tela).
3. Preencha:
   - **Identificador (slug)** — minúsculo, sem espaço, no padrão `algo` ou `algo-com-hifen`. É travado depois de criado.
   - **Nome** — o nome de exibição do plugin.
   - **Ativações padrão (vazio = ilimitado)** — quantos domínios uma licença desse produto pode ativar, quando a licença não define um valor próprio.
   - **WordPress mínimo**, **PHP mínimo**, **Testado até** — opcionais, informativos.
   - **URL do changelog** — opcional.
4. Salve.

{: .example }
> **Exemplo:** cadastrando o V3RHelp — slug `v3rhelp`, nome "V3RHelp", ativações padrão `1` (a maioria dos clientes usa em um site só), WordPress mínimo `6.0`, PHP mínimo `8.0`.

## Dicas e armadilhas

{: .warning }
> **O slug precisa ser exatamente o nome da pasta dentro do zip do plugin.** Quando alguém publicar um release desse produto, o servidor confere se o zip tem uma pasta raiz com esse nome exato — é assim que ele garante que o WordPress vai instalar o plugin certo. Slug `v3r-help` cadastrado para um plugin cujo zip usa a pasta `v3rhelp/` faz **toda publicação falhar**, e só se descobre na hora de publicar, não na hora de cadastrar.

- **Slug é travado depois de criado** — não dá para corrigir um erro de digitação editando; é preciso recadastrar. Confira antes de salvar.
- **"Ativações padrão" vazio não é zero, é ilimitado.** Se o produto deve ter limite, preencha um número — deixar em branco libera ativação sem teto para toda licença desse produto que também não definir um limite próprio.

## Quando dá errado

- **Produto não aparece no formulário de emissão de licença ou no de publicar release** — confira se ele foi realmente salvo (recarregue a aba Produtos) e se você está olhando o produto certo entre vários com nome parecido.

## Limites do papel

Cadastro de produto é feito por qualquer pessoa com acesso ao painel administrativo do V3RLicense — não há papel intermediário aqui, ao contrário dos plugins clientes que têm múltiplos níveis de acesso.
