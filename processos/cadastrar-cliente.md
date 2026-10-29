---
title: Cadastrar cliente
parent: Como faço…
nav_order: 3
---

# Cadastrar cliente

## Por que isto importa

Você raramente precisa cadastrar um cliente por conta própria — **[emitir uma licença](/processos/emitir-licenca/)** já cria o cliente automaticamente se o e-mail informado não existir. Esta tela serve para os casos em que o cadastro automático não basta: corrigir um nome digitado errado, atualizar um e-mail, excluir um cliente antigo que nunca teve licença, ou **[anonimizar](/processos/anonimizar-cliente/)** quando houver pedido de eliminação de dados.

## Passo a passo

1. Abra a aba **Clientes**.
2. Para editar: clique em **Editar** na linha do cliente, ajuste **Nome** e/ou **E-mail**, salve.
3. Para criar manualmente (raro — normalmente a emissão de licença já faz isso): clique em **Novo cliente**, preencha **Nome** e **E-mail**, salve.

## Exemplo

Um cliente pediu para trocar o e-mail cadastrado de `financeiro@exemplo.org.br` para `ti@exemplo.org.br`, porque a caixa antiga foi desativada. Abra Clientes, localize pelo e-mail antigo, edite o campo **E-mail** e salve — as licenças já emitidas continuam vinculadas ao mesmo registro de cliente, só o contato muda.

## Dicas e armadilhas

{: .important }
> **O cadastro automático da emissão de licença busca por e-mail exato.** Se o cliente já existe com `contato@exemplo.com` e uma licença nova é emitida para `Contato@exemplo.com` ou com um espaço a mais, o sistema **não reconhece como o mesmo cliente** — cria um registro novo e duplicado. Revise o e-mail antes de emitir; corrigir depois significa editar manualmente aqui e, se for o caso, reatribuir a licença ao cliente certo.

- **Cliente que tem licença não pode ser excluído** (desde a v0.38.1), em nenhum estado da licença: ativa, vencida, revogada ou arquivada. A tela recusa, lista as licenças e oferece **Anonimizar este cliente**, que tira o nome e o e-mail e preserva o histórico da licença. Nada é revogado nem apagado. Só cliente **sem licença** pode ser excluído, com uma confirmação. Na exclusão em lote, a janela diz quantos serão excluídos e quantos serão recusados, e o resultado separa excluídos, recusados por regra e falhas.
- **Pedido de eliminação de dados não se resolve excluindo:** **[anonimize](/processos/anonimizar-cliente/)**.

## Quando dá errado

- **Cliente anonimizado não pode ser editado nem receber licença nova.** O cadastro fica travado de propósito; se a pessoa voltar a ser cliente, cadastre-a de novo.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel edita e cadastra clientes.
