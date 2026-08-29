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
2. No formulário **Emitir licença manualmente**, escolha **o que a licença cobre**:
   - **Segue uma lista de acesso** — escolha uma [lista de acesso](/processos/gerenciar-lista-acesso/) cadastrada. A licença passa a seguir essa lista: produto acrescentado a ela depois passa a ser coberto automaticamente, sem nova emissão.
   - **Produtos específicos** — marque um ou mais produtos na lista de caixas de seleção. A cobertura fica **fixa** nesse conjunto; produto cadastrado depois não entra sozinho, mesmo que pareça com uma lista de acesso.
3. Preencha o resto:
   - **Cliente** — busque por nome ou e-mail, ou cadastre um novo pelo link **Cadastrar cliente novo**.
   - **Tipo de licença** — define como a expiração é calculada.
   - **Máximo de ativações (vazio = padrão do produto)** — deixe em branco para cada produto coberto usar o próprio padrão; preenchido, o número vale **igualmente para todos os produtos** desta emissão (veja a armadilha abaixo).
   - **Origem**
   - **Anotação (opcional)** — texto livre, útil para registrar o motivo ou o número do pedido.
4. Clique em **Emitir licença**.
5. A chave gerada aparece na confirmação (`Licença emitida: ...`) — copie e entregue ao cliente. É a **mesma chave** que o cliente cola em cada um dos plugins cobertos.

{: .example }
> **Exemplo — licença de um produto só, o caso comercial de hoje:** "Produtos específicos" com só o V3REvent marcado, cliente "Instituto Vida Nova" (`contato@institutovidanova.org.br`), tipo "Anual", ativações padrão do produto, origem "Venda direta", anotação "Pedido #4821 — boleto pago em 20/08".
>
> **Exemplo — parceria com acesso a vários plugins:** "Segue uma lista de acesso" → "Acesso total (parceria)", cliente "GEJA" (`suporte@geja11df.org.br`), tipo "Anual", origem "Isenção — filiada à RIT". A chave emitida ativa V3RLGPD, V3RHelp! e todo produto que entrar na lista depois — sem emitir licença nova a cada plugin novo.

## Dicas e armadilhas

{: .warning }
> **Confira o e-mail antes de emitir.** Se o e-mail não bater exatamente com um cliente já cadastrado (maiúscula/minúscula, espaço, domínio diferente), o V3RLicense **cria um cliente novo** em vez de vincular ao existente — o cliente antigo fica com um histórico, o novo com outro, e ninguém percebe até alguém procurar o cliente errado. Veja **[Cadastrar cliente](/processos/cadastrar-cliente/)** para corrigir se isso já aconteceu.

{: .important }
> **"Máximo de ativações" preenchido substitui o padrão de TODOS os produtos da emissão, não só de um.** Emitir para uma lista com três produtos e preencher "2" aqui dá cota de 2 para os três — mesmo que os produtos tenham padrões diferentes cadastrados (1, 3, 5…). Deixe em branco quando os produtos cobertos devem manter cada um o próprio padrão; só preencha para um caso específico que precisa do mesmo número em tudo.

- **Cliente é criado automaticamente** se o e-mail não existir — você não precisa cadastrá-lo antes.
- **O limite de ativações é contado por produto, não pela licença inteira.** Uma licença cobrindo três produtos tem três contadores separados — ativar o domínio do cliente num dos produtos não consome a cota dos outros dois. Veja **[Licenças](/modulos/licencas/)**.
- **A chave não é reenviada automaticamente** — copie na hora; ela também aparece depois na coluna "Chave" da lista de licenças, então não é perdida, mas você precisa voltar à tela para pegá-la de novo.

## Quando dá errado

- **"Não foi possível emitir a licença — confira produto, nome e e-mail"** — algum campo obrigatório está vazio ou o e-mail não é um e-mail válido.
- Erro de origem ou tipo inválido — normalmente porque a opção selecionada foi desativada por outra pessoa entre você abrir a tela e enviar o formulário. Recarregue e tente de novo.

## Limites do papel

Sem papel intermediário no V3RLicense — qualquer pessoa com acesso ao painel emite licença de qualquer produto.
