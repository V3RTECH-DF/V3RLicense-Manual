---
title: Marcar um produto como gratuito
parent: Como faço…
nav_order: 1.2
---

# Marcar um produto como gratuito

## Por que isto importa

Um plugin gratuito não tem quem comprar nem quem emitir licença, mas ainda precisa **receber atualização pelo próprio WordPress**, como os outros. Marcar o produto como gratuito resolve isso: qualquer site passa a receber as atualizações dele **sem chave de licença**. E, como cada site que pergunta fica registrado, você ganha uma noção de **quantos sites usam o plugin** — algo que um plugin sem licença normalmente não dá.

## Passo a passo

1. Abra **Produtos** e clique em **Editar produto** na linha do plugin (ou crie o produto).
2. Marque **Produto gratuito**.
3. Salve.

A linha do produto passa a mostrar **Gratuito — atualiza sem chave** embaixo do nome e ganha um ícone novo, **Sites do produto gratuito**.

![Formulário do produto com a caixa "Produto gratuito" marcada e a explicação embaixo](/assets/screenshots/produtos-gratuito-marcar.png)

![Lista de produtos: o produto gratuito mostra "Gratuito — atualiza sem chave" e o ícone de globo "Sites do produto gratuito" ao lado dos demais](/assets/screenshots/produtos-lista-gratuito.png)

{: .important }
> **O plugin precisa estar numa versão que saiba pedir atualização sem chave.** Marcar o produto como gratuito prepara o **servidor**; o lado do plugin só consulta sem chave depois que o componente de licenciamento compartilhado que ele usa for atualizado para uma versão nova. Até lá, o plugin continua pedindo uma chave e **marcar a caixa não muda nada para ele**. Antes de contar com o modo gratuito, confirme com quem mantém o plugin que ele já saiu nessa versão.

## Sites do produto gratuito

Clique no ícone **Sites do produto gratuito** para ver quem está usando. A tela mostra:

- **A contagem**, no alto: quantos sites estão no registro, quantos **em produção** e quantos **de teste**.
- **Por site:** o endereço, a **versão instalada**, o **ambiente** (Produção ou Teste), a **primeira vez** e a **última vez** que o site consultou atualização.

![Tela "Sites do produto gratuito": cinco sites, três em produção e dois de teste, com versão instalada e datas da primeira e da última consulta](/assets/screenshots/produtos-sites-gratuitos.png)

### Remover sites do registro

Use o ícone **Remover do registro** na linha, ou marque vários e clique em **Remover selecionados (N)**. O resultado separa concluídos, recusados por regra e falhos.

Remover **não bloqueia o site**: ele continua recebendo atualização e **volta ao registro na próxima consulta**. A remoção serve para limpar a lista (por exemplo, sites de teste que você não quer contar), não para impedir ninguém.

## Exemplo

O "Mural de Avisos" é um plugin gratuito. Você marca **Produto gratuito** e, duas semanas depois, abre **Sites do produto gratuito**: são 140 sites, 118 em produção e 22 de teste. É um número útil para decidir se vale investir numa versão nova — mas é uma estimativa, não uma contagem exata.

## Dicas e armadilhas

- **A contagem é indicativa.** O endereço e a versão são informados pelo próprio site, sem prova; o mesmo site com dois endereços conta duas vezes, e um site que muda de endereço aparece como um novo. Use o número como ordem de grandeza.
- **Desmarcar volta a exigir licença.** Se você tirar a marca, o produto passa a pedir chave como qualquer outro: os sites que já usavam sem chave **deixam de receber atualização** até terem uma licença. Se o produto virou pago, avise antes e emita as licenças primeiro. A tela de sites continua guardando o registro, com um aviso de que o produto já não é gratuito.
- **Não marque um produto pago por engano.** Ele passa a entregar atualização a qualquer um que pedir, sem licença. Confira o produto na lista antes de salvar: a etiqueta verde só aparece nos gratuitos.
- **Marcar "gratuito" não é o mesmo que emitir uma isenção.** A isenção (**[Emitir uma isenção RIT](/processos/emitir-isencao/)**) é uma licença de verdade, concedida a uma organização, com chave e validade. O produto gratuito não tem licença nenhuma.

## Quando dá errado

- **O ícone Sites do produto gratuito não aparece** — o produto não está marcado como gratuito.
- **A lista de sites está vazia** — nenhum site consultou atualização ainda. Se o plugin já foi publicado, confirme que ele está numa versão que consulta sem chave (veja o aviso acima).
- **"Este produto não está marcado como gratuito: hoje ele exige licença"** — você abriu a lista de um produto que deixou de ser gratuito; os sites mostrados são o registro de quando ainda era.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel marca, desmarca e remove sites. Como desmarcar corta a atualização de quem usa sem chave, trate como uma decisão de produto, não como ajuste de cadastro.
