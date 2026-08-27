---
title: Cadastrar cliente
parent: Como faço…
nav_order: 3
---

# Cadastrar cliente

## Por que isto importa

Você raramente precisa cadastrar um cliente por conta própria — **[emitir uma licença](/processos/emitir-licenca/)** já cria o cliente automaticamente se o e-mail informado não existir. Esta tela serve para os casos em que o cadastro automático não basta: corrigir um nome digitado errado, atualizar um e-mail, ou excluir um cliente antigo.

## Passo a passo

1. Abra a aba **Clientes**.
2. Para editar: clique em **Editar** na linha do cliente, ajuste **Nome** e/ou **E-mail**, salve.
3. Para criar manualmente (raro — normalmente a emissão de licença já faz isso): clique em **Novo cliente**, preencha **Nome** e **E-mail**, salve.

## Exemplo

Um cliente pediu para trocar o e-mail cadastrado de `financeiro@exemplo.org.br` para `ti@exemplo.org.br`, porque a caixa antiga foi desativada. Abra Clientes, localize pelo e-mail antigo, edite o campo **E-mail** e salve — as licenças já emitidas continuam vinculadas ao mesmo registro de cliente, só o contato muda.

## Dicas e armadilhas

{: .important }
> **O cadastro automático da emissão de licença busca por e-mail exato.** Se o cliente já existe com `contato@exemplo.com` e uma licença nova é emitida para `Contato@exemplo.com` ou com um espaço a mais, o sistema **não reconhece como o mesmo cliente** — cria um registro novo e duplicado. Revise o e-mail antes de emitir; corrigir depois significa editar manualmente aqui e, se for o caso, reatribuir a licença ao cliente certo.

- **Excluir um cliente com licença vinculada é recusado.** Não é possível excluir por engano um cliente que ainda tem histórico de licença — a tela recusa a exclusão nesse caso, em vez de apagar em cascata.

## Quando dá errado

- **"Excluir" não teve efeito e o cliente continua na lista** — ele tem licença vinculada. Verifique nas licenças filtrando pelo nome/e-mail dele.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel edita e cadastra clientes.
