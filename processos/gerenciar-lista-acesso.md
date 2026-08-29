---
title: Gerenciar listas de acesso
parent: Como faço…
nav_order: 1.5
---

# Gerenciar listas de acesso

## Por que isto importa

Antes desta funcionalidade, uma licença cobria **um** produto só — cliente com direito a vários plugins recebia uma chave por plugin. O parque real da casa hoje é **11 organizações** (entre parceiras e filiadas à RIT) com direito a **todos** os plugins: isso são **88 licenças** emitidas uma a uma, e mais 11 a cada plugin novo publicado.

Uma lista de acesso resolve o "mais 11 a cada plugin novo": é um conjunto nomeado de produtos ("Acesso total (parceria)", "Filiada RIT"…) que uma licença pode **seguir**. Acrescentar um plugin à lista estende a cobertura de todas as licenças que a seguem, na hora — sem visitar licença por licença.

## Antes de começar

A lista nasce vazia. Você cria a lista, depois acrescenta os produtos a ela — em duas etapas, não uma.

## Passo a passo — criar a lista

1. Abra a aba **Listas de acesso**.
2. Preencha **Identificador (slug)** e **Rótulo exibido**.
3. Deixe **Ativa** marcado se a lista deve aparecer já no formulário de emissão.
4. Clique em **Criar lista**.

## Passo a passo — acrescentar ou remover produto

1. Na linha da lista, clique no ícone de lista de tarefas (gerenciar produtos).
2. Em **Disponíveis para acrescentar**, clique **Acrescentar** no produto desejado — ou, em **Nesta lista**, clique **Remover** no que deve sair.
3. Feche o modal.

{: .example }
> **Exemplo:** a lista "Acesso total (parceria)" cobre hoje V3RLGPD e V3RHelp!. Ao publicar o V3RProp, você acrescenta o V3RProp à lista uma única vez — e as 11 organizações que seguem essa lista passam a ter acesso ao V3RProp automaticamente, sem tocar em nenhuma das 11 licenças.

## Dicas e armadilhas

{: .important }
> **Acrescentar produto vale na hora, para todas as licenças que seguem a lista.** Não é preciso confirmar licença a licença — é o comportamento que faz o plugin novo custar uma ação em vez de onze. Se isso não é o que você quer para um caso específico, emita aquela licença marcando produtos **específicos**, não seguindo uma lista (veja **[Emitir uma licença](/processos/emitir-licenca/)**).

{: .warning }
> **Remover produto de uma lista NÃO tira o acesso de quem já o tinha.** Só impede que licenças que venham a seguir a lista **depois** da remoção recebam aquele produto. Para tirar o acesso de alguém que já tem, é preciso agir na licença dela, não na lista.

- **Lista inativa some do formulário de emissão**, mas não afeta quem já a segue — as licenças continuam recebendo produtos acrescentados à lista, mesmo com ela desativada para novas emissões.
- **Lista com pelo menos uma licença seguindo não pode ser excluída.** Desative em vez de excluir se ela não deve mais ser usada em emissões novas.
- **O limite de ativações continua por produto**, não pela licença inteira ou pela lista — cada produto coberto herda o próprio padrão cadastrado nele. Veja **[Emitir uma licença](/processos/emitir-licenca/)**.

## Quando dá errado

- **Botão Excluir recusado / desabilitado** — a lista tem licença seguindo. Confira a coluna "Licenças seguindo" na listagem; desative em vez de excluir.
- **Produto não aparece em "Disponíveis para acrescentar"** — ou ele já está "Nesta lista", ou ainda não foi cadastrado em **[Registrar um plugin novo](/processos/cadastrar-produto/)**.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel cria, edita e gerencia produtos de qualquer lista de acesso.

## Glossário

**Lista de acesso**
: Conjunto nomeado de produtos que uma licença pode seguir. Editável a qualquer momento; a mudança nunca é implícita — sempre um ato deliberado nesta tela.

**Seguir uma lista**
: Modo de emissão em que a cobertura da licença acompanha a lista escolhida, incluindo produtos acrescentados depois. Alternativa a marcar produtos específicos, que fixa a cobertura no momento da emissão.
