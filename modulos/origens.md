---
title: Origens
parent: Telas do painel
nav_order: 5
---

# Origens

Veja o passo a passo em **[Cadastrar tipo de licença e origem](/processos/cadastrar-tipo-e-origem/)**.

![Lista de origens cadastradas: "Isenção — filiada à RIT" (Concedida) e "Venda (WooCommerce)" (Gera cobrança), ambas com status Ativa](/assets/screenshots/origens-cobranca.png)

## Colunas da listagem

Identificador (slug) · Rótulo exibido · Cobrança (**Gera cobrança** / **Concedida**) · Status (Ativa/Inativa).

## Campos do formulário

Identificador (slug, travado depois de criado) · Rótulo exibido · **Gera cobrança** (marque para origem de venda; deixe desmarcado para origem concedida, sem pagamento) · Ativa (aparece no formulário de emissão).

{: .important }
> **O que "Gera cobrança" decide.** É essa marcação — não o nome da origem — que separa licença cobrada de licença concedida em três pontos: quem recebe o aviso de vencimento (cliente × operador, veja **[Configurações](/modulos/configuracoes/)**), se a licença entra em carência/suspensão ao vencer ou vai direto para expirada (veja **[Como funciona a licença](/como-funciona/)**), e se ela pode ser suspensa por falta de pagamento. **O padrão de origem nova é desmarcado (não cobra).** Marcar de menos deixa de avisar um cliente pagante — recuperável, é só corrigir o cadastro; marcar de mais arrisca suspender quem nunca teve cobrança nenhuma.

## Ações

Editar · Excluir (recusado quando a origem está em uso por alguma licença — desative em vez de excluir).
