---
title: Anonimizar um cliente
parent: Como faço…
nav_order: 3.5
---

# Anonimizar um cliente

## Por que isto importa

Quando uma pessoa pede que seus dados sejam eliminados (direito previsto na LGPD) e o cliente dela **tem licença**, o cadastro não pode ser excluído — e, desde a v0.38.1, o painel nem deixa: ao tentar excluir, ele recusa e oferece **Anonimizar este cliente** no lugar. O histórico da licença precisa ser guardado por cinco anos (veja **[Política de Privacidade](/legal/privacidade/)**). O que não precisa ser guardado é a **identificação da pessoa** por trás desse histórico.

**Anonimizar** faz exatamente essa separação: o nome e o e-mail somem, a licença e as ativações continuam existindo.

{: .warning }
> **É irreversível.** Depois de anonimizar não há como recuperar o nome nem o e-mail, nem pela tela nem com apoio técnico. Confirme que o pedido é legítimo e que veio de quem pode fazê-lo antes de clicar.

## Quando usar

- **Pedido de eliminação de dados** de um cliente que tem licença vinculada. É o caso para o qual a ação existe.
- **Não use** para corrigir nome ou e-mail digitado errado (isso é **Editar**, em **[Cadastrar cliente](/processos/cadastrar-cliente/)**) nem como forma de "limpar" a lista de clientes.
- **Cliente sem nenhuma licença** também pode ser anonimizado, mas nesse caso costuma bastar excluir.
- **Você tentou excluir um cliente que tem licença** e a tela recusou: é o caminho certo. Clique em **Anonimizar este cliente** na própria janela, ou use o ícone de anonimizar da linha.

## O que muda e o que não muda

| Muda | Não muda |
|---|---|
| Nome e e-mail do cadastro viram marcadores ("Cliente anonimizado" com o número do cadastro e um e-mail que não existe) | As licenças do cliente: continuam com o mesmo estado, a mesma chave e as mesmas ativações |
| O destinatário e o texto de erro do registro de envio de e-mails da chave são apagados | O **usuário do WordPress** da pessoa — não é apagado |
| O nome gravado dentro dos tokens de acesso a serviço é apagado | Os **pedidos do WooCommerce** — não são apagados; pertencem à loja e têm prazo próprio |
| O vínculo do cadastro com a conta WordPress é desfeito | |
| O cliente anonimizado deixa de poder receber licença nova ou reenvio de chave | |

Se também for preciso eliminar o usuário do WordPress e os pedidos, isso é feito **nas telas do WordPress e da loja**, não aqui. A própria janela de confirmação avisa disso.

## Passo a passo

1. Abra **Clientes** e localize o cadastro.
2. Clique no ícone **Anonimizar cliente** (o olho riscado, em vermelho) da linha. (Se você tentou **Excluir** e a tela recusou por haver licença, o botão **Anonimizar este cliente** da janela de recusa leva ao mesmo passo.)
3. A janela de confirmação mostra o nome e o e-mail que serão substituídos, **quantas licenças** estão vinculadas e o aviso de que a ação é irreversível.
4. Se alguma licença do cliente tem **anotação**, ela é listada ali, com o texto. **Leia cada uma** e escolha:
   - **Limpar estas anotações** — apaga o texto das anotações (e das observações de revogação) dessas licenças.
   - **Manter as anotações como estão** — não mexe nelas.

   O botão de confirmar só habilita depois da escolha.
5. Clique em **Anonimizar definitivamente**.
6. A tela confirma: quantas licenças foram preservadas e em quantas as anotações foram limpas. A linha do cliente passa a mostrar **Anonimizado em** e a data, e perde os ícones de editar e anonimizar.

![Janela "Anonimizar cliente": aviso de ação irreversível, uma licença afetada, a anotação da licença listada com o texto e as opções Limpar ou Manter](/assets/screenshots/clientes-anonimizar-confirma.png)

![Lista de clientes depois da anonimização: a linha "Cliente anonimizado" com a data e o e-mail de marcador, sem os ícones de editar e anonimizar](/assets/screenshots/clientes-anonimizado-lista.png)

## Exemplo

A Cooperativa Mãos Unidas pede a eliminação dos dados do contato dela. O cadastro tem uma licença anual, e na anotação dela alguém escreveu, tempos atrás, o nome e o telefone da pessoa que cuidava do assunto. Você abre **Anonimizar cliente**, lê a anotação, vê que ela só tem dado pessoal e escolhe **Limpar estas anotações**. Depois de confirmar, a licença continua valendo e atualizando normalmente, mas já não existe nenhum jeito de saber quem era o contato.

## Dicas e armadilhas

- **A anotação é onde o dado pessoal costuma escapar.** O campo é livre e ninguém garante o que foi colado ali. Por isso o sistema não decide por você: se escolher **Manter** sem ler, o nome que estava na anotação continua gravado, e o pedido de eliminação não foi atendido por inteiro. Só mantenha uma anotação depois de ler e ter certeza de que ela não identifica ninguém.
- **Não existe anonimização em lote, de propósito.** Cada cliente exige a leitura das anotações dele; um botão para vários tiraria justamente essa leitura. Na exclusão em lote, os clientes recusados por terem licença ganham o atalho para anonimizar **um de cada vez**.
- **Anonimizar não resolve o pedido sozinho.** Se a pessoa também tem usuário no site e pedidos na loja, esses dados continuam lá. Combine com quem administra o WordPress e a loja o que fazer em cada um.
- **Não anonimize para "desfazer" um cadastro errado.** Cliente com e-mail duplicado ou nome trocado se corrige editando; anonimizado, o cadastro não volta.

## Quando dá errado

- **O ícone Anonimizar cliente não aparece na linha** — o cadastro já foi anonimizado.
- **"Não foi possível preparar a anonimização."** — a janela de confirmação não carregou as informações do cliente. Recarregue a tela e tente de novo; nada foi alterado.
- **"Falha ao anonimizar o cliente."** — a operação não terminou. Confira a lista: se o cliente não aparece como "Anonimizado em…", nada mudou e dá para repetir.
- **Ao tentar emitir licença ou reenviar chave para o cliente anonimizado** — o sistema recusa, com mensagem própria. É o esperado: o cadastro já não tem e-mail para onde enviar.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel pode anonimizar. Justamente por isso, e por ser irreversível, trate como decisão que precisa de um pedido registrado, não como rotina.
