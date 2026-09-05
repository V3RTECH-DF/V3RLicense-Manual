---
title: Produtos
parent: Telas do painel
nav_order: 3
---

# Produtos

Veja o passo a passo em **[Registrar um plugin novo](/processos/cadastrar-produto/)**.

![Lista dos sete produtos cadastrados, com identificador, nome, ativações padrão e versões mínimas de WordPress e PHP](/assets/screenshots/produtos-lista.png)

## Colunas da listagem

Identificador (slug) · Nome · Ativações padrão · WP mínimo · PHP mínimo.

## Campos do formulário

Identificador (slug, travado depois de criado) · Nome · Ativações padrão (vazio = ilimitado) · WordPress mínimo (opcional) · PHP mínimo (opcional) · Testado até (opcional) · URL do changelog (opcional) · **Serviço da casa (opcional — token de acesso)**, desde a v0.30.0.

{: .note }
> **"Serviço da casa" liga o produto a uma audiência de serviço** (veja **[Audiências de serviço](/modulos/audiencias-de-servico/)**) — quando preenchido, toda venda desse produto passa a emitir também um token de acesso ao serviço escolhido (hoje, o V3RSigner), junto da licença normal. Deixe em branco para um produto que só é plugin, sem token — é o caso da imensa maioria. Veja **[Token de acesso a serviço da casa](/como-funciona/#token-de-acesso-a-serviço-da-casa)**.

## Ações

**Venda do plugin** (ícone de loja) — leva à tela de **[Venda do plugin](/modulos/venda-do-plugin/)**, onde se cadastra tanto o plano por assinatura (combinações de duração e sites) quanto a licença perpétua ou a venda negociada, cada uma na sua seção.

{: .note }
> **"PHP mínimo" não é decorativo.** É o valor que o servidor manda no aviso de atualização — se o PHP do site do cliente for menor, o WordPress dele não oferece a atualização, sem erro visível. Veja **[Registrar um plugin novo](/processos/cadastrar-produto/)** e **[Diagnóstico: cliente diz que não atualiza](/processos/diagnostico-sem-atualizacao/)**.
