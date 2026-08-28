---
title: Novidades
nav_order: 7
---

# Novidades

O que mudou no V3RLicense, versão a versão, em linguagem simples. Para o histórico técnico completo, veja o changelog do projeto.

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
