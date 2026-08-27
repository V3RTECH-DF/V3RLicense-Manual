---
title: Publicar uma versão
parent: Como faço…
nav_order: 10
---

# Publicar uma versão

## Por que isto importa

Publicar é o que faz o cliente com licença ativa receber o aviso de atualização no wp-admin dele. Existem dois caminhos — pela pipeline de CI (token) ou manualmente pela tela — e **os dois passam pela mesma conferência**, para nunca divergir sobre o que é aceito.

## A conferência tripla, e por que ela existe

Antes de aceitar um release, o V3RLicense confere que **três fontes de versão concordam entre si**:

1. a versão que você declarou (no formulário, ou no corpo da requisição da pipeline);
2. a versão no **nome do arquivo** do zip (`slug-vX.Y.Z.zip` ou `slug-X.Y.Z.zip`);
3. a versão no **cabeçalho `Version:`** do arquivo `.php` principal, dentro do zip.

Também confere que o zip tem, na raiz, uma **pasta com o slug exato do produto** — é por essa pasta que o WordPress instala o plugin.

{: .important }
> **Por que a conferência existe:** é o que impede publicar um pacote trocado — um zip renomeado às pressas, um build antigo reaproveitado com nome novo, uma pasta com nome errado que instalaria por cima do plugin errado. Se qualquer uma das três versões divergir, ou a pasta não bater com o slug, a publicação é recusada — nada é salvo pela metade.

## Passo a passo — pela tela (manual)

1. Abra a aba **Releases**.
2. Selecione o **Produto** no seletor do topo.
3. No formulário **Publicar release**, preencha:
   - **Produto**
   - **Versão** (ex.: `1.2.3`)
   - **Arquivo .zip**
   - **Changelog (opcional)**
4. Clique em **Publicar release**.

## Passo a passo — pela pipeline (token)

1. Gere um token em **[Gerenciar tokens de publicação](/processos/gerenciar-tokens-publicacao/)**, se ainda não existir um para essa pipeline.
2. Na pipeline de CI, faça uma requisição autenticada com o token ao endpoint de publicação, enviando `product_slug`, a versão e o arquivo zip do build.
3. O resultado segue a mesma validação da tela — sucesso ou erro, sem etapa manual no meio.

## Exemplo

Publicando a versão `1.24.0` do V3REvent pela tela: produto "V3REvent", versão `1.24.0`, arquivo `v3revent-v1.24.0.zip` (com a pasta `v3revent/` na raiz e o `.php` principal com `Version: 1.24.0` no cabeçalho), changelog "Corrige exportação de relatório em PDF quando o evento não tem patrocinador". As três versões (`1.24.0` no formulário, `1.24.0` no nome do arquivo, `1.24.0` no cabeçalho) concordam — publica.

## Dicas e armadilhas

- **A versão no formulário só precisa bater com as outras duas — não define nada por si só.** Se você digitar `1.24.0` mas o zip foi gerado como `1.24.1`, a publicação falha; corrija o campo do formulário ou gere o zip de novo, mas não force a publicação editando só um dos três.
- **Versão duplicada é recusada** — não é possível publicar duas vezes a mesma versão de um produto. Se precisar corrigir um release já publicado, veja **[Remover um release publicado](/processos/remover-release/)** antes de publicar de novo com o mesmo número.

## Quando dá errado

| Mensagem | O que significa | O que fazer |
|---|---|---|
| "Versão inválida — use o formato semântico (ex.: 1.2.3 ou 1.2.3-beta.1)" | o campo Versão não está no formato esperado | corrija o número |
| "Já existe um release publicado com esta versão" | versão duplicada para o produto | confira se não é a mesma publicação repetida; se for correção, remova o release antigo primeiro |
| "Não foi possível identificar a versão no NOME do arquivo — esperado algo como 'slug-vX.Y.Z.zip'" | o nome do zip não segue o padrão | renomeie o arquivo antes de subir |
| "A versão declarada diverge da versão no NOME do arquivo" | formulário e nome do zip não batem | corrija um dos dois |
| "O zip não tem a pasta 'slug/' na raiz — o WordPress instala o plugin pelo nome dessa pasta" | a pasta raiz dentro do zip não é o slug do produto | corrija o build, ou confira se o slug do produto está certo (veja **[Registrar um plugin novo](/processos/cadastrar-produto/)**) |
| "Não foi encontrado, dentro de 'slug/', um arquivo .php com cabeçalho 'Version:'" | nenhum `.php` de primeiro nível tem o cabeçalho padrão do WordPress | confira se o build não removeu o cabeçalho do arquivo principal do plugin |
| "A versão declarada diverge da versão no CABEÇALHO do plugin dentro do zip" | o `Version:` do `.php` principal não bate com o formulário/nome do arquivo | atualize o cabeçalho no código-fonte do plugin antes de gerar o zip |
| Erro de upload (arquivo excedeu o tamanho máximo) | o zip é maior do que o servidor aceita | avise o time técnico — pode exigir ajuste de configuração do servidor |

## Limites do papel

Sem papel intermediário no V3RLicense. A pipeline de CI age com o escopo do token (só publicar) — veja **[Gerenciar tokens de publicação](/processos/gerenciar-tokens-publicacao/)**.
