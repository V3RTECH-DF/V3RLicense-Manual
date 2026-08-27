---
title: Emitir uma licença
parent: Como faço…
nav_order: 4
---

# Emitir uma licença

## Por que isto importa

Emitir a licença é o que dá ao cliente a chave que ele cola no plugin — sem isso, o plugin dele não recebe atualização (veja **[Como funciona a licença](/como-funciona/)**). É a ação mais frequente deste painel.

## Antes de começar

O produto, ao menos uma origem ativa e ao menos um tipo de licença ativo precisam existir. Se algum faltar, veja **[Registrar um plugin novo](/processos/cadastrar-produto/)** e **[Cadastrar tipo de licença e origem](/processos/cadastrar-tipo-e-origem/)**.

## Passo a passo

1. Abra a aba **Licenças**.
2. No formulário **Emitir licença manualmente**, preencha:
   - **Produto**
   - **Nome do cliente**
   - **E-mail do cliente**
   - **Tipo de licença** — define como a expiração é calculada.
   - **Máximo de ativações (vazio = padrão do produto)** — deixe em branco para usar o padrão cadastrado no produto.
   - **Origem**
   - **Anotação (opcional)** — texto livre, útil para registrar o motivo ou o número do pedido.
3. Clique em **Emitir licença**.
4. A chave gerada aparece na confirmação (`Licença emitida: ...`) — copie e entregue ao cliente.

{: .example }
> **Exemplo:** produto "V3REvent", cliente "Instituto Vida Nova" (`contato@institutovidanova.org.br`), tipo "Anual", ativações padrão do produto, origem "Venda direta", anotação "Pedido #4821 — boleto pago em 20/08".

## Dicas e armadilhas

{: .warning }
> **Confira o e-mail antes de emitir.** Se o e-mail não bater exatamente com um cliente já cadastrado (maiúscula/minúscula, espaço, domínio diferente), o V3RLicense **cria um cliente novo** em vez de vincular ao existente — o cliente antigo fica com um histórico, o novo com outro, e ninguém percebe até alguém procurar o cliente errado. Veja **[Cadastrar cliente](/processos/cadastrar-cliente/)** para corrigir se isso já aconteceu.

- **Cliente é criado automaticamente** se o e-mail não existir — você não precisa cadastrá-lo antes.
- **"Máximo de ativações" em branco não é zero** — usa o padrão do produto (que também pode ser ilimitado, se o produto não define um).
- **A chave não é reenviada automaticamente** — copie na hora; ela também aparece depois na coluna "Chave" da lista de licenças, então não é perdida, mas você precisa voltar à tela para pegá-la de novo.

## Quando dá errado

- **"Não foi possível emitir a licença — confira produto, nome e e-mail"** — algum campo obrigatório está vazio ou o e-mail não é um e-mail válido.
- Erro de origem ou tipo inválido — normalmente porque a opção selecionada foi desativada por outra pessoa entre você abrir a tela e enviar o formulário. Recarregue e tente de novo.

## Limites do papel

Sem papel intermediário no V3RLicense — qualquer pessoa com acesso ao painel emite licença de qualquer produto.
