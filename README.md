# V3RLicense — Manual

Manual do usuário do V3RLicense. Público.

Faz parte do container `V3RTECH/V3RLicense`, que reúne também `Code/`
(código do servidor) e `Projeto/` (documentação e gestão). Publicado no
GitHub Pages, domínio próprio: <https://docs.v3rlicense.v3rtech.com.br>

## Para quem é este manual

Para a equipe V3RTECH/RIT, em dois papéis: quem **opera** o V3RLicense
(emite licença, cadastra produto, gera token de publicação, resolve chamado
de "meu plugin não atualiza") e quem **desenvolve** um plugin da casa e
precisa prepará-lo para o licenciamento e a auto-atualização — ver
[`integrar-plugin/`](integrar-plugin/index.md). **Não** é para o cliente
final que instalou um plugin licenciado por aqui — esse nunca entra no
V3RLicense; o que ele precisa saber mora na aba de licença do próprio
plugin.

A exceção é a página **[Como funciona a licença](como-funciona.md)**, que
descreve a política de licenciamento em si e é a referência que os manuais
de cada plugin (V3REvent, V3RHelp, V3RLGPD, GE Associados, RIT360 Solidário,
RIT360 Premiado…) apontam quando o cliente final quer entender a própria
licença.

## A coisa mais importante para entender sobre a licença

O que a licença dá direito é a **atualizações e correções** do plugin — não a
uma funcionalidade extra. Isso significa duas coisas:

- **Se a licença vencer, o plugin continua funcionando normalmente.** Nada é
  bloqueado, nenhuma tela para de abrir. O que muda é que o plugin deixa de
  receber novidades e correções até a licença ser renovada.
- Manter a licença ativa é o que garante que o plugin continue recebendo
  melhorias e, principalmente, correções de segurança.

Se a organização é filiada à RIT, a licença é gratuita e não exige nenhuma
etapa de compra — veja `processos/emitir-isencao.md`.

## Estado

Conteúdo escrito por completo (índice, primeiros passos, política de
licenciamento, 14 páginas de processo, referência por tela — incluindo
licença cobrindo mais de um produto e listas de acesso (V3RLicense-Code#26)
e a integração com o WooCommerce: produtos vendáveis, carência/suspensão,
avisos automáticos e renovação em lote (V3RLicense-Code#2) —, FAQ,
novidades cobrindo até a v0.16.1, legal, mais a seção `integrar-plugin/`
para quem desenvolve) e ilustrado com as capturas de
`assets/screenshots/`. Falta só o modal do token recém-gerado (não
capturável sem gerar um token real em produção) — descrito em palavras em
[`modulos/tokens-de-publicacao.md`](modulos/tokens-de-publicacao.md). A
seção `integrar-plugin/` não tem captura — é material de código, sem tela
própria a ilustrar.

A v0.14.0–v0.16.1 (30/08/2026) acrescentou a aba "Minhas licenças" na
conta do cliente no site (V3RLicense-Code#34) — cliente vê a própria
licença, desativa um site sozinho e recebe o caminho de volta a valer;
documentado em `como-funciona.md`, com o campo novo de Configurações, a
nota em `processos/liberar-ativacao.md` e as FAQs correspondentes. **Sem
captura ainda** — a versão está sendo publicada durante esta redação; ver
lista de telas pendentes no relatório desta passada.
