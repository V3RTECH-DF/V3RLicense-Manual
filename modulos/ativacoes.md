---
title: Ativações
parent: Telas do painel
nav_order: 2
---

# Ativações

Tela de detalhe, acessada a partir de uma licença em **Licenças**. Veja o passo a passo em **[Liberar uma ativação](/processos/liberar-ativacao/)**.

![Ativações de uma licença que cobre três plugins: o mesmo domínio aparece uma vez por plugin, distinguido pela coluna Produto](/assets/screenshots/ativacoes-lista.png)

## Colunas da listagem

| Coluna | O que mostra |
|---|---|
| Domínio | domínio ativado |
| Produto | plugin a que aquela ativação pertence — só aparece quando a licença cobre mais de um produto |
| Ambiente de teste | sim/não — não conta na cota quando "sim" |
| Versão do plugin | versão instalada no cliente |
| Último contato | data/hora da última consulta ao servidor |
| Status | ativo / desativado |

Numa licença que cobre um produto só, a coluna Produto continua aparecendo, sempre com o mesmo nome — e o filtro não aparece, porque não há o que filtrar.

## Filtro por produto

Quando a licença cobre mais de um plugin, a tela mostra um filtro que lista só os produtos daquela licença. Aplicando o filtro, aparece ao lado a cota daquele plugin (usadas / limite, ou "ilimitada"). Sem filtro, nenhuma cota aparece — mostrar um número único somaria produtos com limites diferentes, e o total não representaria nada.

O cabeçalho da tela acompanha: numa licença de vários produtos, ele deixa de nomear um plugin específico e passa a dizer quantos produtos ela cobre.

![Filtro por produto aplicado: a tela mostra só as ativações daquele plugin, com a cota dele ao lado do filtro](/assets/screenshots/ativacoes-filtro-produto.png)

## Ações

Desativar domínio (linha a linha e em lote) — só disponível em linhas ainda ativas.

{: .tip }
> **O mesmo domínio pode aparecer mais de uma vez** — uma linha por produto que ele ativou daquela licença. Confira a coluna Produto (ou o filtro aplicado) antes de desativar: desativar a linha errada libera a vaga do plugin errado, e o cliente continua sem conseguir ativar o que precisava. A confirmação de desativação nomeia o domínio e o produto, mas o hábito é conferir antes de clicar, não só na hora de confirmar.
