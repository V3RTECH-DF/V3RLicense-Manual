---
title: Emitir uma isenção RIT
parent: Como faço…
nav_order: 5
---

# Emitir uma isenção RIT

## Por que isto importa

Organizações do terceiro setor filiadas à RIT recebem licença gratuita, por política da casa. O V3RLicense não tem uma tela dedicada a isso — é o mesmo formulário de emissão de licença, usando a origem certa. Isso importa saber porque não há nada "diferente" para procurar: é questão de escolher os campos certos.

{: .note }
> **Renovação automática é roadmap, não realidade hoje.** Não existe verificação automática contra uma fonte externa de filiação — a validade é controlada manualmente, do mesmo jeito que qualquer outra licença anual (V3RLicense-Code#4). Não prometa ao cliente uma renovação automática.

## Passo a passo

1. Confirme com quem decide (hoje, verificação manual da filiação à RIT) que a organização está apta.
2. Abra a aba **Licenças** e preencha o formulário **Emitir licença manualmente**, exatamente como em **[Emitir uma licença](/processos/emitir-licenca/)**, com duas diferenças:
   - **O que a licença cobre** — se a organização tem direito ao catálogo inteiro (o caso mais comum de filiada RIT), escolha **Segue uma lista de acesso** e a lista correspondente (ex.: "Filiada RIT"). Se o direito é a um plugin só, use **Produtos específicos**.
   - **Origem** = "Isenção — filiada à RIT" (ou o rótulo equivalente cadastrado).
   - **Tipo de licença** = normalmente "Anual", para forçar uma revisão anual da filiação — mas confirme se sua organização decidiu diferente para este caso.
3. Emita normalmente.

![Formulário "Emitir licença manualmente" com "Segue uma lista de acesso" selecionado e uma licença emitida para GEJA cobrindo V3RLGPD, V3RHelp! e mais 1, origem "Isenção — filiada à RIT"](/assets/screenshots/licencas-emitir-lista-acesso.png)

{: .example }
> **Exemplo (o mesmo da captura acima):** lista de acesso "Acesso total (parceria)", cliente "GEJA" (`suporte@geja11df.org.br`), tipo "Anual", origem "Isenção — filiada à RIT", anotação "Filiação à RIT confirmada em 12/08/2026." — registrando **quem** confirmou é ainda melhor, quando o formulário permitir texto livre maior. Com a lista, a chave cobre todos os produtos dela hoje **e** os que forem acrescentados depois, sem nova emissão.

## Dicas e armadilhas

{: .tip }
> **Emitir por lista de acesso é o que evita reemitir a isenção a cada plugin novo.** Antes, uma organização filiada com direito ao catálogo inteiro recebia uma chave por plugin; seguindo a lista "Filiada RIT" (ou equivalente), ela recebe uma chave só, e um plugin novo publicado passa a valer para ela assim que alguém acrescenta o produto à lista — veja **[Gerenciar listas de acesso](/processos/gerenciar-lista-acesso/)**.

{: .tip }
> **Use a anotação para registrar como a filiação foi confirmada e quando.** Como não há checagem automática, esse texto é o único rastro de por que a isenção foi concedida — importante se alguém precisar auditar depois.

{: .warning }
> **A renovação também é manual.** Quando a licença de isenção vencer, alguém precisa lembrar de conferir se a organização continua filiada antes de renovar — veja **[Renovar uma licença](/processos/renovar-licenca/)**. Não existe aviso automático de "está na hora de revisar esta filiação".

## Quando dá errado

Os mesmos casos de **[Emitir uma licença](/processos/emitir-licenca/)** — não há validação adicional específica para isenção, porque o mecanismo é o mesmo.

## Limites do papel

Sem papel intermediário no V3RLicense. A decisão de *quem* pode confirmar filiação é de processo interno da casa, não do sistema.
