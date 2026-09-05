---
title: Configurações
parent: Telas do painel
nav_order: 11
---

# Configurações

![Tela de Configurações com a seção "Aviso ao operador" e o campo E-mail do operador preenchido com suporte@v3rtech.com.br](/assets/screenshots/configuracoes-email-operador.png)

Tela de configuração geral do plugin — nasce pequena, só com o endereço que recebe o aviso de vencimento das licenças **concedidas** (isenções). É aqui que as próximas configurações do V3RLicense vão morar conforme o produto crescer.

## Por que isto importa

Licença comprada avisa o **cliente** por e-mail quando está perto de vencer (veja **[Como funciona a licença](/como-funciona/)**). Licença **concedida** (isenção, cortesia) segue outra regra: o cliente dela nunca recebe e-mail — quem é avisado é **o operador**, porque a renovação dessas licenças é sempre manual, feita por quem opera o V3RLicense.

## Campos

**E-mail do operador** — o endereço que recebe esse aviso. Vem preconfigurado com `suporte@v3rtech.com.br`; troque se o time responsável por renovar isenções mudar.

**Página com os produtos disponíveis** (desde a v0.16.0) — uma página do site, escolhida aqui pelo gestor. Ela é usada na aba **"Minhas licenças"** do cliente (veja **[Como funciona a licença](/como-funciona/)**) quando o produto original de uma licença **saiu de venda ou foi despublicado**: em vez de virar um link quebrado, a aba explica que aquele produto não está mais disponível para contratação e oferece essa página, mais o contato.

## Por que isto importa

Licença comprada avisa o **cliente** por e-mail quando está perto de vencer (veja **[Como funciona a licença](/como-funciona/)**). Licença **concedida** (isenção, cortesia) segue outra regra: o cliente dela nunca recebe e-mail — quem é avisado é **o operador**, porque a renovação dessas licenças é sempre manual, feita por quem opera o V3RLicense.

## Passo a passo

1. Abra a aba **Configurações**.
2. Preencha **E-mail do operador**.
3. Se quiser, escolha a **Página com os produtos disponíveis**.
4. Clique em **Salvar**.

## Dicas e armadilhas

{: .tip }
> **Use a [renovação em lote](/processos/renovar-licenca/) para agir sobre o aviso.** O e-mail que chega aqui já sugere isso — regularizar todas as licenças concedidas vencendo de uma vez, em vez de uma por uma.

- **Deixar o campo de e-mail com um endereço que ninguém lê é a forma mais comum de perder o prazo de uma isenção sem perceber** — o aviso sai certinho, só que para a caixa errada.
- **Deixar a página de produtos disponíveis vazia não quebra nada** — o cliente cuja licença cobre um produto descontinuado ainda vê o contato. Mas é oportunidade perdida: quem estava disposto a pagar de novo não recebe nenhuma alternativa, só um e-mail para escrever.

## Chave de assinatura

![Card "Chave de assinatura" em Configurações, mostrando a fonte em uso, a chave pública e os botões Exportar chave privada e Importar](/assets/screenshots/configuracoes-chave-assinatura.png)

É a chave que assina **tudo o que o V3RLicense emite e confere** — licença, resposta de validação e, desde a v0.30.0, o token de acesso a serviço da casa. Não é uma configuração do dia a dia: existe para dois momentos específicos, backup e recuperação.

### Por que isto importa

{: .important }
> **O arquivo exportado aqui é o segredo mais sensível do V3RLicense.** Quem tiver essa chave privada consegue emitir licença válida e token válido **em nome da V3RTECH**, de fora do sistema, sem deixar rastro na tela de nenhum dos dois. Trate como trataria a senha mestra de um banco: nunca por e-mail, nunca em chat, nunca em repositório de código — só em cofre de segredo.

### Fonte em uso

O plugin resolve a chave nesta ordem, e mostra qual delas está valendo: **variável de ambiente**, **constante em `wp-config.php`**, e só na ausência das duas, **banco de dados** — nesse último caso, o próprio plugin gera e guarda a chave, cifrada com as chaves de segurança do `wp-config.php` do site. Exportar e importar, aqui na tela, é a via de backup e recuperação **só dessa chave gravada no banco** — quem já define a chave por variável de ambiente ou constante gerencia o backup dela por fora, no próprio mecanismo de segredo do servidor.

### Exportar

Baixa a chave privada **ativa** no momento (a que a tela mostra em "Fonte em uso"), em base64. Guarde em local seguro — veja o aviso acima. Use antes de uma migração de servidor, ou como cópia de recuperação periódica.

### Importar

Substitui a chave gravada no **banco de dados** pela colada aqui. Não afeta a chave de variável de ambiente ou de constante — se uma das duas estiver definida, ela continua sendo a fonte em uso mesmo depois de importar; a chave importada só passa a valer se as outras duas fontes forem removidas.

{: .warning }
> **Importar uma chave diferente da que assinou os tokens já emitidos avisa o cliente, mas não invalida nada na hora.** Quem já tem um token instalado continua funcionando — a conta do cliente mostra um aviso de que a chave de assinatura mudou e que a cadeia exibida na tela já reflete a chave nova, mas que a cópia instalada continua válida e atualizar é opcional. Troque a chave só quando tiver certeza — rotação de chave sem necessidade real só gera pergunta de suporte.

### Quando dá errado

**"A chave gravada no banco não pôde ser decifrada"** — as chaves de segurança do `wp-config.php` mudaram desde que a chave foi gravada (comum depois de restaurar um site em outro ambiente). Importe a chave salva em outro lugar (o backup que você tirou por **Exportar**, antes da mudança) ou gere uma chave nova — nesse segundo caso, avise os clientes com token vinculado a certificado, porque a chave pública muda.

**"nenhuma — assinatura indisponível"** em Fonte em uso — nenhuma das três fontes está configurada e a chave nunca chegou a ser gerada. Emissão de licença, validação e token de serviço ficam indisponíveis até isso ser corrigido; importe uma chave existente ou aguarde o plugin gerar uma sozinha na próxima operação que precisar dela.
