---
title: Licenças e acessos
parent: Telas do painel
nav_order: 1
---

# Licenças e acessos

Veja o passo a passo em **[Emitir uma licença ou acesso](/processos/emitir-licenca/)**, **[Renovar](/processos/renovar-licenca/)** (individual e em lote), **[Revogar](/processos/revogar-licenca/)** e **[Emitir uma isenção RIT](/processos/emitir-isencao/)**. Sobre o token de um acesso, veja **[Gerenciar tokens de serviço](/processos/gerenciar-tokens-de-servico/)**. Sobre a cobertura por lista, veja **[Gerenciar listas de acesso](/processos/gerenciar-lista-acesso/)** e **[Listas de acesso](/modulos/listas-de-acesso/)**. Sobre os status de carência e suspensão, veja **[Como funciona a licença](/como-funciona/)**.

![Formulário "Emitir licença manualmente" com a escolha "Segue uma lista de acesso" / "Produtos específicos", e uma linha de licença cobrindo V3RLGPD, V3RHelp! e mais 1, com ativações listadas por produto](/assets/screenshots/licencas-emitir-lista-acesso.png)

![Lista de licenças mostrando a coluna Cobertura (produtos cobertos e a lista de acesso seguida, quando houver) e a coluna Ativações detalhada por produto](/assets/screenshots/licencas-cobertura.png)

![Cartões de estatística no topo da tela: total de licenças, ativas, suspensas por falta de pagamento e revogadas](/assets/screenshots/licencas-cards-status.png)

![Lista de licenças mostrando os cinco status lado a lado: Ativa, Revogada, Expirada, Suspensa por falta de pagamento e Em carência](/assets/screenshots/licencas-status-novos.png)

{: .note }
> Estas quatro capturas ainda mostram a tela **antes** da unificação da v0.33.0 — a coluna **Categoria** e as ações de token na linha, descritas abaixo, ainda não aparecem nelas. Recaptura pendente, ver `README.md`.

## Licença ou acesso — a mesma tela, dois vocabulários

Desde a v0.33.0, um produto ligado a um **serviço da casa** (veja **[Audiências de serviço](/modulos/audiencias-de-servico/)**) deixou de ser chamado de "licença". O que ele emite chama-se **acesso** — "este acesso vence em…", "emitir acesso", "token deste acesso". Um produto que só é plugin continua sendo **licença**, do jeito de sempre.

Não são duas telas: é a **mesma listagem**, com a coluna **Categoria** dizendo qual é qual, linha a linha. Não confunda Categoria com a coluna **Tipo** — Tipo é a periodicidade da licença (Mensal, Anual…); Categoria é o que o item representa (Licença de plugin ou Acesso a serviço). As duas colunas existem lado a lado e respondem perguntas diferentes.

{: .tip }
> **Filtre por Categoria** quando quiser olhar só um dos dois — por exemplo, para auditar quantos acessos a um serviço estão ativos, sem o ruído das licenças de plugin comuns na mesma lista.

Uma licença cobre **um ou mais produtos** — desde a licença de um cliente comum, que continua cobrindo um produto só, até a licença de uma parceria que segue uma lista de acesso e cobre todo o catálogo. Veja **[Emitir uma licença ou acesso](/processos/emitir-licenca/)** para a diferença entre seguir uma lista e marcar produtos específicos.

## Colunas da listagem

| Coluna | O que mostra |
|---|---|
| Chave | `license_key` |
| Cobertura | os produtos cobertos; se a licença segue uma lista, o nome da lista aparece abaixo dos produtos |
| Cliente | nome e e-mail |
| Categoria | **Licença** (plugin) ou **Acesso** (serviço da casa) — não confundir com a coluna Tipo, abaixo |
| Status | Ativa / Em carência / Suspensa por falta de pagamento / Expirada / Revogada — veja **[Como funciona a licença](/como-funciona/)** para o que diferencia carência de suspensão |
| Ativações | usadas / máximo (ou "ilimitado") **por produto** — uma linha por produto coberto, quando são vários |
| Expira em | data, ou "sem validade" |
| Origem | rótulo cadastrado |
| Tipo de licença | a periodicidade (Mensal, Anual…) — rótulo cadastrado |
| Token de acesso | só preenchida numa linha de **Acesso**: a trava (Sem trava/Certificado/Organização) e a validade, ou "Não emitido" quando o acesso ainda não tem token. **Nunca o valor do token em claro** — quem vê é só o cliente, na própria conta |

## Filtros

Status, Produto (filtra licenças que cobrem aquele produto, mesmo cobrindo outros também), Cliente (nome ou e-mail), **Categoria** (Todos / Só licenças / Só acessos).

## Indicadores de trava, no topo

Três cartões mostram quantos **tokens ativos** existem hoje em cada trava — Sem trava, Com certificado, Por organização (reservada para uso futuro) — somando todos os acessos da conta, sem depender do filtro aplicado. É o mesmo indicador que a antiga tela separada de tokens mostrava; aqui ele acompanha a listagem unificada.

## Emitir — uma ação só, mesmo quando sai token junto

O formulário de emissão muda de nome sozinho conforme o que você escolhe:

- Escolhendo só produto(s) de **licença** (plugin comum), o formulário e o botão dizem **"Emitir licença"**.
- Escolhendo produto **ligado a um serviço da casa**, dizem **"Emitir acesso"** — e o **token sai junto, na mesma ação**, sem precisar de uma segunda tela nem de uma venda antes.
- Escolhendo uma lista de acesso que mistura os dois tipos de produto (caso raro), o formulário fica com o rótulo neutro **"Emitir licença ou acesso"**.

Antes da v0.32.0, só compra e renovação emitiam token — se você precisasse dar acesso a alguém fora do fluxo de venda, não tinha caminho manual. Hoje o operador emite pelo painel exatamente como emitiria uma licença comum. Veja o passo a passo completo, com os campos do formulário, em **[Emitir uma licença ou acesso](/processos/emitir-licenca/)**.

{: .important }
> **Nunca existem dois tokens vigentes para o mesmo acesso.** Emitir de novo quando já existe um vigente é recusado — o caminho para trocar é **reemitir**, na linha do acesso ou pela própria conta do cliente, nunca uma segunda emissão.

## Ações do token, na linha do acesso

Só uma linha de **Acesso** mostra ações de token, e só quando fizer sentido para o estado dela:

- **Emitir token de acesso** — aparece quando o acesso ainda não tem token vigente (por exemplo, foi emitido antes de o produto ganhar audiência, ou o token anterior foi revogado sem substituto). Confirma e emite na hora.
- **Revogar token de acesso** — aparece quando já existe um token vigente. Revoga sem emitir outro no lugar; o consumidor do serviço para de aceitar aquele token em **até 1 hora** (a janela de propagação da lista de cancelados), não imediatamente.

Marcando mais de uma linha de acesso com token, aparece **Revogar tokens selecionados (N)** para revogar em lote. Veja o passo a passo com exemplos em **[Gerenciar tokens de serviço](/processos/gerenciar-tokens-de-servico/)**.

{: .warning }
> **Você nunca vê o valor do token aqui — só os metadados** (trava e validade). A cadeia em claro só existe na conta do próprio cliente, na aba "Minhas licenças". Se o cliente perdeu o valor, ele mesmo copia de novo na própria conta — não existe "reenviar token" para o suporte fazer.

## Campos do formulário de emissão

O que a licença/acesso cobre (Segue uma lista de acesso / Produtos específicos), Cliente, Tipo de licença, Máximo de ativações (vazio = padrão de cada produto), Origem, Anotação (opcional).

## Ações

Ver ativações · Renovar licença (também renova o token, quando é um acesso — veja **[Renovar uma licença](/processos/renovar-licenca/)**) · Revogar licença/acesso (linha a linha e em lote) · Emitir/Revogar token de acesso, só na linha de um acesso. Selecionando mais de uma licença aparecem os botões **Renovar selecionadas** e **Revogar selecionadas**; a confirmação do lote avisa quando a seleção mistura tipos de licença diferentes, porque cada uma renova com o próprio vencimento (veja **[Renovar uma licença](/processos/renovar-licenca/)**).
