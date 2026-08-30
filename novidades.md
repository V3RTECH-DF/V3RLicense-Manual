---
title: Novidades
nav_order: 7
---

# Novidades

O que mudou no V3RLicense, versão a versão, em linguagem simples. Para o histórico técnico completo, veja o changelog do projeto.

## v0.13.0 — 29/08/2026

- **Carência, suspensão e régua de avisos por e-mail.** Licença que gera cobrança e vence entra em **carência por 15 dias** antes de ser suspensa — dois status novos ("Em carência" e "Suspensa por falta de pagamento"), separados de "Expirada" e "Revogada". Suspensa não derruba nada no plugin do cliente: só para de receber atualização e correção, a mesma regra de sempre. O cliente passa a receber e-mail avisando o vencimento com antecedência (que varia pelo tipo de licença), mais os avisos durante a carência; quem tem assinatura ativa recebe um único aviso, 7 dias antes. **Licença concedida (isenção) avisa o operador, nunca o cliente** — para o endereço configurável na nova tela **[Configurações](/modulos/configuracoes/)**. Estorno **total** de um pedido revoga a licença; estorno **parcial** não mexe nela. Cancelar uma assinatura também não revoga nada — o cliente mantém acesso até o fim do período já pago. Veja **[Como funciona a licença](/como-funciona/)**.
- **Correção:** a carência terminava algumas horas antes do fim do dia 15, então quem vencia de manhã perdia o acesso no mesmo dia em que o e-mail dizia "é hoje que acaba". Corrigido para terminar sempre no fim do dia 15.

## v0.12.0 — 29/08/2026

- **Assinatura recorrente renova a mesma licença**, sem duplicar — cada cobrança paga estende a licença já emitida (mesma chave, mesmas ativações), em vez de criar uma segunda. Renovação automática não manda e-mail (o WooCommerce já confirma a cobrança ao cliente).
- **Renovar licenças em lote**, na tela de Licenças — selecione várias e renove de uma vez; a confirmação avisa quando a seleção mistura tipos de licença diferentes, porque cada uma vence numa data própria. Veja **[Renovar uma licença](/processos/renovar-licenca/)**.
- **Correção:** um pedido de assinatura feito à mão no painel, ou com o produto duplicado/editado depois, não emitia licença nem e-mail nem deixava registro do motivo — a checagem perguntava a pergunta errada ("o tipo é periódico?" em vez de "este pedido está numa assinatura?").

## v0.11.0 — 29/08/2026

- **Compra paga emite a licença sozinha e manda a chave por e-mail** — uma licença por unidade comprada, vinculada ao pedido que pagou. O cliente é sempre identificado pela conta com que fez o pedido, nunca por e-mail digitado à parte. Veja **[Como funciona a licença](/como-funciona/)**.

## v0.10.0 — 29/08/2026

- **Produtos vendáveis** — nova tela que liga um produto do V3RLicense a um tipo de licença e o publica na loja WooCommerce. Nasce **em rascunho e sem preço**: o operador define o preço e publica na loja depois. Publicar de novo ajusta o mesmo produto; trocar o tipo de licença reclassifica entre avulso e assinatura; excluir o cadastro **não** apaga o produto já publicado na loja. Veja **[Cadastrar um produto vendável](/processos/cadastrar-produto-vendavel/)**.
- **Correção:** reclassificar um produto vendável (de avulso para assinatura, ou o inverso) não trocava de fato o tipo do produto na loja, por causa de um cache interno do WooCommerce — e ainda relatava sucesso.

## v0.9.0 — 29/08/2026

- **Origem passa a declarar se gera cobrança.** Cada origem (venda, isenção, cortesia…) agora tem um campo próprio, visível na tela, que diz se a licença emitida por ela é vendida ou concedida — é o que decide quem recebe o aviso de vencimento e se a licença pode ser suspensa por falta de pagamento. Veja **[Origens](/modulos/origens/)**.

## v0.8.2 — 29/08/2026

- **Correção:** com uma licença cobrindo vários produtos, a tela de Ativações não dizia de qual produto era cada linha — desativar a ativação errada virou possível. Cada linha agora mostra o produto, com filtro por produto e a cota correspondente.

## v0.8.1 — 29/08/2026

- **Correção:** em sete lugares da tela (inclusive a coluna "Ambiente de teste" de Ativações), um valor desligado vindo do banco aparecia como ligado — o dado nunca esteve errado, mas a tela mentia. Centralizado num único ponto de leitura.

## v0.8.0 — 29/08/2026

- **Uma licença passa a cobrir vários produtos**, com **listas de acesso** nomeadas — um conjunto de produtos (ex.: "Acesso total (parceria)") que a licença pode seguir; acrescentar um produto à lista estende a cobertura, na hora, de toda licença que a segue. Onze organizações parceiras que hoje exigiam 88 licenças (uma por plugin, por organização) passam a precisar de 12; o próximo plugin publicado custa acrescentá-lo à lista, não emitir 11 licenças novas. Veja **[Emitir uma licença](/processos/emitir-licenca/)** e **[Listas de acesso](/modulos/listas-de-acesso/)**.
- **Correção:** reclassificar um produto vendável não trocava o tipo do produto na loja nos dois sentidos.

## v0.7.1 — 28/08/2026

- **Correção:** excluir um cliente com licenças era impossível, mesmo depois de revogá-las — a checagem não distinguia licença revogada de licença ativa. A exclusão agora revoga automaticamente as licenças pendentes, mostra a lista antes (com a chave mascarada) e pede confirmação dupla quando há algo a revogar.
- **Correção:** o ícone de busca sobrepunha o texto no campo de escolher cliente.

## v0.7.0 — 28/08/2026

- **Ícone do produto na tela de atualização do cliente** — plugins nossos deixam de aparecer com a peça de quebra-cabeça genérica do WordPress quando há atualização disponível. Requer a v3r-core 0.7.0 ou superior no plugin do cliente.
- **Emitir licença passa a escolher um cliente já cadastrado**, por busca de nome/e-mail, em vez de digitar os dados de novo. Reduz o risco de criar um cliente duplicado por um e-mail digitado com pequena diferença.

## v0.6.1 — 27/08/2026

- **Todos os plugins da casa passam a exigir PHP 8.2.** Um site abaixo dessa versão deixa de receber atualização — de forma silenciosa, sem erro visível — e um plugin ativado nesse PHP se autodesativa e avisa o administrador do site com o mínimo exigido e o instalado. Veja **[Diagnóstico: cliente diz que não atualiza](/processos/diagnostico-sem-atualizacao/)**, que ganhou um passo novo por causa disso.
- **Correção:** a checagem de PHP insuficiente do próprio V3RLicense não funcionava direito num site realmente desatualizado — em vez de mostrar o aviso claro, o site quebrava com erro fatal. Agora, PHP abaixo do exigido sempre resulta em aviso legível, nunca em tela quebrada.
- **Correção de bastidor:** o V3RLicense passou a ter verificação automática (CI) a cada mudança de código — sem efeito visível para quem usa o painel.

## v0.6.0 — 27/08/2026

- **Token de publicação passou a valer para um produto só.** Antes, um token vazado podia publicar release de qualquer um dos produtos cadastrados; agora, cada token é preso ao produto escolhido na criação (ou, opcionalmente, a "Todos os produtos", de forma explícita — nunca por omissão). Veja **[Gerenciar tokens de publicação](/processos/gerenciar-tokens-publicacao/)**.
- **Correção:** um token com escopo errado agora recebe uma mensagem de erro própria, diferente da de "token inválido" — evita confundir "a credencial está certa, mas para o produto errado" com "a credencial não existe mais".

## v0.5.0 — 27/08/2026

- **Publicação por token, para pipeline automática.** Além de publicar release pela tela, agora dá para publicar por uma credencial de máquina (token) — pensada para pipelines de CI publicarem sozinhas, sem depender de alguém abrir o painel. Veja **[Gerenciar tokens de publicação](/processos/gerenciar-tokens-publicacao/)**.
- **Correção de bastidor:** um problema de instalação do banco de dados que só aparecia em certas formas de atualizar o servidor foi corrigido — sem efeito visível para quem usa o painel.

## v0.4.0 — 26/08/2026

- **Cadastro próprio de tipo de licença e origem.** Antes de emitir uma licença, você escolhe o tipo (mensal, anual, perpétua…) e a origem (venda, cortesia, isenção…) entre cadastros próprios — não mais um texto solto. As quatro telas de cadastro (Produtos, Clientes, Origens, Tipos) já nasceram com seleção em lote.
- **Regra de renovação mais justa.** Renovar em dia conta a partir do vencimento anterior; renovar atrasado conta a partir de hoje — quem renova em dia não perde nem ganha tempo por atraso de outra pessoa.
- **Correção:** a tela de licenças passou a mostrar o nome da origem, em vez de um código técnico.

## v0.3.0 — 26/08/2026

- **Publicação de release, com conferência tripla.** A tela de Releases nasceu — cadastrar versão, subir o zip, e o servidor confere que a versão declarada, o nome do arquivo e o cabeçalho do plugin dentro do zip concordam entre si, antes de aceitar. Veja **[Publicar uma versão](/processos/publicar-uma-versao/)**.
- **Correção:** a checagem de atualização passou a comparar versões de verdade (não a data de publicação) — republicar uma correção antiga não faz mais um cliente "regredir" sem querer.

## v0.1.0 — 25/08/2026

- **Lançamento.** Emissão de licença, ativação por domínio, validação, checagem de atualização e download — o núcleo do servidor de licenças da V3RTECH e da RIT.
- **Correção de segurança:** um ponto que permitia, em tese, ler arquivo fora do que deveria no servidor foi fechado antes de qualquer uso indevido.
