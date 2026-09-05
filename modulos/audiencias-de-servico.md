---
title: Audiências de serviço
parent: Telas do painel
nav_order: 9.5
---

# Audiências de serviço

Veja o passo a passo em **[Cadastrar uma audiência de serviço](/processos/cadastrar-audiencia-de-servico/)**.

![Lista de audiências de serviço com o rótulo "V3RSigner", o identificador (slug) v3rsigner e o status Ativa](/assets/screenshots/audiencias-de-servico-lista.png)

Cada linha desta lista é um **serviço da casa que aceita token de acesso** — hoje, só o V3RSigner, mas a tela já nasce pronta para o próximo. Cadastrar aqui não emite nenhum token sozinho: é o **produto**, em **[Produtos](/modulos/produtos/)**, que se liga a uma audiência para que a compra desse produto passe a emitir token junto da licença. Produto sem audiência ligada (a imensa maioria) nunca gera token — nada muda para ele.

## Colunas da listagem

Rótulo · Identificador (slug) · Status (Ativa/Inativa).

## Campos do formulário

**Identificador (slug)** — minúsculo, sem espaço, no padrão `algo` ou `algo-com-hifen`. É o valor gravado dentro de cada token (o `aud`, "audiência", no jargão de quem verifica o token do outro lado) — é por ele que o serviço reconhece "este token é para mim". Travado depois de criado.

**Rótulo** — o nome de exibição, o que aparece nesta lista e nos filtros de **[Tokens de serviço](/modulos/tokens-de-servico/)**.

**Ativa** — só uma audiência ativa aceita revogação por lista de cancelados consultável pelo serviço; desativar não apaga os tokens já emitidos, mas tira a audiência do cadastro corrente para novas ligações de produto.

{: .warning }
> **Excluir uma audiência não é reversível pela tela**, e o slug fica gravado dentro de todo token já emitido para ela. Antes de excluir, confira se algum produto ainda está ligado a ela em **[Produtos](/modulos/produtos/)** — produto órfão de audiência para de emitir token nas próximas vendas, em silêncio.
