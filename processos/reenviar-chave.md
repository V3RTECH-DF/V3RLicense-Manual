---
title: Reenviar a chave por e-mail
parent: Como faço…
nav_order: 7.5
---

# Reenviar a chave por e-mail

## Por que isto importa

Quem compra um plugin recebe a chave por e-mail. Se esse e-mail não chega — o cliente digitou o endereço errado, o servidor de e-mail recusou, caiu no spam —, ele tem uma licença paga e nenhum jeito de ativá-la. Antes da v0.37.0 você só descobria isso quando o cliente reclamava. Agora cada licença mostra **se a chave foi enviada, para quem e quando**, e existe um lugar que lista só o que falhou, para você resolver antes de ele perguntar.

## Ver se a chave foi enviada

Na lista de **Licenças e acessos**, logo abaixo da chave de cada **licença de plugin** há uma linha pequena com uma de quatro situações:

| O que aparece | O que significa |
|---|---|
| **Chave enviada a** (e-mail) **em** (data) | O e-mail saiu para o servidor de e-mail sem erro. |
| **Chave enviada a** (e-mail) **no mesmo envio do pedido** | O pedido tinha várias chaves e elas foram juntas num e-mail só; este é o e-mail dessa licença. |
| **Falha no envio a** (e-mail)**:** (erro) — em vermelho | O servidor recusou. O texto depois dos dois-pontos é o erro devolvido por ele. |
| **Envio da chave não registrado** | Não há registro de envio — licença emitida antes de o sistema registrar, ou emitida pelo painel, que não manda e-mail de chave. |

{: .note }
> **"Enviada" quer dizer "o servidor aceitou", não "o cliente leu".** Se o cliente jura que não recebeu e o registro diz enviada, olhe primeiro o spam e confirme se o e-mail do cadastro dele está certo (veja **[Cadastrar cliente](/processos/cadastrar-cliente/)**).

**Acesso a serviço** não tem essa linha: ele não recebe e-mail de chave (o cliente pega o token na própria conta).

![Lista de licenças com a linha de envio da chave sob cada chave: uma enviada com e-mail e data, três com "Falha no envio" e o erro em vermelho, e três com "Envio da chave não registrado"](/assets/screenshots/licencas-lista-revogacao-envio.png)

## Reenviar a chave de uma licença

1. Na linha da licença, clique no ícone de envelope **Reenviar chave**.
2. Confirme em **Reenviar**. O aviso diz que o e-mail vai para o **e-mail atual do cliente** e que o reenvio fica registrado como um envio novo.
3. A tela responde uma de três coisas:
   - **Chave reenviada.**
   - **Não havia o que reenviar (licença revogada ou cliente sem e-mail).**
   - **O reenvio falhou:** (o erro do servidor).

![Janela de confirmação "Reenviar chave", explicando que o e-mail vai para o e-mail atual do cliente e fica registrado como um envio novo](/assets/screenshots/licencas-reenviar-chave.png)

O ícone fica desabilitado em licença revogada e não aparece em acesso a serviço.

## Reenviar o que falhou, de uma vez

1. Na lista de licenças, clique em **Envios da chave com falha** (canto superior direito).
2. A tela lista cada envio que falhou e ainda não foi refeito, com a(s) chave(s), o cliente e o e-mail, o **Erro** e **Quando**. Um envio pode cobrir várias chaves do mesmo pedido.
3. Reenvie um só (ícone de envelope na linha) ou marque vários (ou o quadradinho do cabeçalho, para todos) e clique em **Reenviar selecionados (N)**.
4. Confirme. O resultado aparece em uma linha: **Enviados: X. Recusados: Y. Falhos: Z.**

![Tela "Envios da chave com falha" com três envios listados, um marcado, o botão Reenviar selecionados (1) e as colunas Chave(s), Cliente, Erro e Quando](/assets/screenshots/envios-com-falha.png)

O envio que dá certo sai da lista sozinho. Se você não vê nada, a mensagem é **Nenhum envio da chave com falha pendente.** — é o resultado que se quer.

### O que cada número do resultado quer dizer

| Número | Significado | O que fazer |
|---|---|---|
| **Enviados** | O servidor aceitou o e-mail. | Nada. |
| **Recusados** | O sistema nem tentou: todas as licenças do envio já estão revogadas, o cliente não tem e-mail no cadastro, ou aquele envio já não estava mais pendente (alguém resolveu antes). | Confira o cadastro do cliente e o status das licenças. |
| **Falhos** | O sistema tentou e o servidor recusou de novo. | O envio continua na lista. Leia o erro: se é do servidor de e-mail, não adianta reenviar de novo antes de corrigi-lo. |

## Exemplo

Marcos Tavares comprou duas licenças no mesmo pedido e escreveu o e-mail com um erro de digitação. Na lista, a linha dele mostra em vermelho "Falha no envio a marcos.tavares@example.com: …". Você abre **Clientes**, corrige o endereço, volta a **Envios da chave com falha**, reenvia — e o e-mail sai para o endereço **corrigido**, com as duas chaves.

## Dicas e armadilhas

- **O reenvio vai para o e-mail que está no cadastro hoje, não para o que falhou.** É o que faz a correção funcionar — mas, se você reenviar sem corrigir o cadastro, vai falhar de novo, agora com uma segunda linha de falha no histórico. Corrija o endereço primeiro.
- **Licença revogada nunca recebe a chave de novo.** Num envio com várias chaves, as revogadas ficam de fora e as demais vão normalmente. Isso evita entregar a chave de uma licença que já não vale; se o cliente precisa de uma, **[emita uma nova](/processos/emitir-licenca/)**.
- **Reenviar de dentro da licença cobre só aquela chave.** Se o pedido tinha três e você reenvia uma, as outras duas continuam com o registro antigo — reenvie pela tela de falhas quando quiser refazer o envio inteiro.
- **Não reenvie em série "para garantir".** Cada reenvio é um e-mail a mais na caixa do cliente e uma linha a mais no registro.

## Quando dá errado

- **"Não havia o que reenviar (licença revogada ou cliente sem e-mail)"** — confira o status da licença e o e-mail do cliente em **Clientes**.
- **"O reenvio falhou: …"** — o texto é o erro do servidor de e-mail do site. Erros do tipo "Could not instantiate mail function" ou "SMTP connect() failed" são do servidor, não do cadastro: fale com quem cuida do e-mail do site antes de tentar de novo.
- **A licença diz "Envio da chave não registrado" e o cliente já tem a chave** — esperado em licença antiga; não é falha e não aparece na tela de falhas.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel reenvia. O reenvio só chega ao e-mail do cadastro; não existe campo para mandar a chave para outro endereço (corrija o cadastro, se for o caso).
