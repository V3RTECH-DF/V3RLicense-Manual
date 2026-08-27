---
title: Primeiros passos
nav_order: 2
---

# Primeiros passos

O V3RLicense é o plugin WordPress que roda no site que hospeda o servidor de licenças (`v3rtech.com.br`). Você não instala nada por conta própria — ele já está instalado e ativo. Este guia é o caminho da primeira vez que você abre o painel até emitir a primeira licença.

## 1. Onde fica o painel

Acesse `https://v3rtech.com.br/wp-admin/` e faça login com sua conta de administrador. No menu lateral do WordPress, o item **V3RLicense** abre o painel — uma aplicação de página única com sete abas, uma por tipo de cadastro.

![Menu lateral do WordPress com o item V3RLicense destacado em azul, entre Plugins e Hello](/assets/screenshots/menu-wp-admin.png)

## 2. As sete abas, em ordem de uso

| Aba | Para que serve |
|---|---|
| **Licenças** | emitir, listar, renovar e revogar licenças |
| **Produtos** | cadastrar os plugins que o servidor licencia |
| **Clientes** | ver e editar quem recebeu licença |
| **Origens** | os motivos de emissão (venda, cortesia, isenção RIT…) |
| **Tipos de licença** | as periodicidades (mensal, anual, perpétua…) |
| **Tokens de publicação** | credenciais que publicam release, para pipeline de CI |
| **Releases** | as versões publicadas de cada produto, por onde você também publica manualmente |

{: .tip }
> **A ordem importa na primeira vez.** Produtos, Origens e Tipos de licença são cadastro-base: a tela de Licenças só emite para o que já existe ali. Antes de emitir a primeira licença de um plugin novo, ele precisa estar cadastrado em Produtos — veja **[Registrar um plugin novo](/processos/cadastrar-produto/)**.

## 3. Cadastro mínimo antes da primeira licença

Se o produto que você vai licenciar ainda não existe no servidor:

1. Abra **[Registrar um plugin novo](/processos/cadastrar-produto/)** e cadastre o produto.
2. Confira se já existe ao menos uma **origem** e um **tipo de licença** ativos (a instalação já vem com alguns pré-cadastrados) — se não, veja **[Cadastrar tipo de licença e origem](/processos/cadastrar-tipo-e-origem/)**.
3. Agora sim, **[emita a primeira licença](/processos/emitir-licenca/)**.

{: .warning }
> **Cliente é criado automaticamente ao emitir.** Você não precisa cadastrar o cliente antes — se o e-mail informado não existir ainda, o V3RLicense cria o registro na hora. Isso tem uma consequência: **e-mail digitado errado na emissão cria um cliente novo e duplicado**, em vez de vincular ao cliente certo. Veja o alerta completo em **[Emitir uma licença](/processos/emitir-licenca/)**.

## 4. Depois de emitida a primeira licença

A licença emitida tem uma **chave** (`license_key`) — é isso que você entrega ao cliente para ele colar no campo de licença do plugin dele. A partir daí:

- O plugin cliente consulta o servidor para **validar** a própria licença (ver **[Como funciona a licença](/como-funciona/)**).
- Quando o cliente ativa o plugin num domínio, isso conta como **uma ativação** — acompanhe em **[Liberar uma ativação](/processos/liberar-ativacao/)**.
- Quando você publica uma versão nova do plugin, o cliente com licença válida recebe o aviso de atualização automaticamente — ver **[Publicar uma versão](/processos/publicar-uma-versao/)**.

## Próximo passo

Leia **[Como funciona a licença](/como-funciona/)** — é a política que sustenta todas as decisões operacionais deste manual, e a página que você vai linkar quando um cliente perguntar "por que minha licença venceu e o plugin continua funcionando?".
