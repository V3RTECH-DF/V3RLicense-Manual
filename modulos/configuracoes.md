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

O plugin resolve a chave nesta ordem, e mostra qual delas está valendo: **variável de ambiente**, **constante em `wp-config.php`**, e só na ausência das duas, **banco de dados** — nesse último caso, o próprio plugin gera e guarda a chave no banco, cifrada com uma **chave-mestra própria dele**: um arquivo que o plugin cria sozinho numa pasta protegida dentro da pasta de uploads do site (`uploads/v3rlicense/signing-key`). Exportar, importar e gerar nova, aqui na tela, são a via de backup e recuperação **só dessa chave gravada no banco** — quem já define a chave por variável de ambiente ou constante gerencia o backup dela por fora, no próprio mecanismo de segredo do servidor.

{: .note }
> **A troca periódica das chaves de segurança do WordPress não afeta mais a chave de assinatura.** Plugins de segurança costumam trocar essas chaves de tempos em tempos, e antes (até a v0.35.x) isso deixava a chave gravada no banco ilegível. Desde a v0.36.0 a chave de assinatura não depende delas: a chave-mestra é um arquivo do próprio plugin, e o que muda no `wp-config.php` passa batido. Uma chave gravada no formato anterior que ainda abre é migrada para o formato novo sozinha, na primeira leitura, sem trocar a chave.

### Aviso de backup pendente

Enquanto a chave em uso **não for exportada**, o card mostra um aviso em destaque: *"Esta chave de assinatura ainda não tem cópia de segurança"*. O aviso não bloqueia nada — o plugin segue assinando normalmente —, mas ele é sério: exporte a chave e guarde o arquivo no cofre de segredo **antes de qualquer outra coisa**. Essa cópia é a **única forma de recuperar a chave** se o arquivo da chave-mestra se perder (por exemplo, ao restaurar o banco do site sem a pasta de uploads — veja a armadilha mais abaixo). Sem ela, a única saída é gerar uma chave nova, e isso exige reinstalar o plugin em todos os sites clientes.

### Exportar

Baixa a chave privada **ativa** no momento (a que a tela mostra em "Fonte em uso"), em base64. Guarde em local seguro — veja o aviso acima. Use antes de uma migração de servidor, ou como cópia de recuperação periódica. **Na primeira vez que abrir esta tela e ver o aviso de backup pendente, não é opcional:** exporte e guarde no cofre.

### Importar

Substitui a chave gravada no **banco de dados** pela colada aqui. Não afeta a chave de variável de ambiente ou de constante — se uma das duas estiver definida, ela continua sendo a fonte em uso mesmo depois de importar; a chave importada só passa a valer se as outras duas fontes forem removidas.

{: .warning }
> **Importar uma chave diferente da que assinou os tokens já emitidos avisa o cliente, mas não invalida nada na hora.** Quem já tem um token instalado continua funcionando — a conta do cliente mostra um aviso de que a chave de assinatura mudou e que a cadeia exibida na tela já reflete a chave nova, mas que a cópia instalada continua válida e atualizar é opcional. Troque a chave só quando tiver certeza — rotação de chave sem necessidade real só gera pergunta de suporte.

### Gerar nova chave

O botão **Gerar nova chave** (em vermelho, abaixo de Importar) substitui a chave gravada no banco por um par novo — inclusive quando a atual está ilegível. Ele pede confirmação antes de agir, e a confirmação diz o que está em jogo; leia com calma.

{: .warning }
> **Gerar nova chave troca a chave pública, e isso quebra todo plugin cliente que conhece a chave antiga.** Cada plugin cliente leva a chave pública embutida no código e só aceita respostas do servidor assinadas pela chave que ele conhece. Com a chave nova, **ativação, validação e verificação de atualização deixam de funcionar** em todos os sites clientes — eles passam a recusar as respostas deste servidor — até o plugin ser **reinstalado numa versão que traga a chave nova**. **Isso não chega por atualização automática**: é reinstalação, site por site. A chave antiga deixa de existir aqui; só um backup exportado antes a recupera.

**Use só em último caso:** a chave atual está ilegível **e** não há backup exportado para importar. Havendo backup, **importe** — é o caminho que não quebra ninguém. Se a chave só parece "velha" ou você quer trocar por higiene, não gere: o que você ganha não compensa reinstalar o plugin em todos os clientes. Decidiu gerar mesmo assim? Exporte a chave nova assim que ela aparecer (o aviso de backup pendente volta) e avise o time de suporte antes, porque as primeiras reclamações chegam em minutos.

### Armadilha: restaurar o site a partir de backup

{: .important }
> **Ao restaurar o site, restaure o banco E a pasta de uploads, juntos.** A chave de assinatura está no banco, mas só abre com o arquivo da chave-mestra, que mora na pasta de uploads (`uploads/v3rlicense/signing-key`). Restaurar só o banco — ou restaurar o banco de um ponto e a pasta de uploads de outro — deixa a chave **ilegível**: o plugin para de assinar e o painel mostra o aviso vermelho descrito abaixo. O contrário também vale: um backup só da pasta de uploads não traz a chave, que está no banco.

Isso é intencional: um dump do banco sozinho, vazado, não abre a chave. O preço é que backup incompleto vira problema — e é por isso que a cópia exportada (aviso de backup pendente, acima) é obrigatória, não um capricho.

### Quando dá errado

**"A chave gravada no banco não pôde ser aberta"** (aviso vermelho no topo do card; a *Fonte em uso* aparece como "nenhuma — assinatura indisponível") — a chave existe, mas o plugin não consegue lê-la, e enquanto isso **não assina nada**: `/activate`, `/validate` e `/update-check` falham. Há duas causas possíveis, e a recuperação é a mesma:

- **O arquivo da chave-mestra sumiu ou é de outra instalação** — o caso típico é restaurar o banco sem a pasta de uploads (ou com a de outro ambiente), ou a pasta `uploads/v3rlicense/signing-key` ter sido apagada numa limpeza.
- **A chave é antiga, gravada no formato anterior à v0.36.0**, cifrada com as chaves de segurança do `wp-config.php`, e essas chaves **já mudaram** antes de o plugin migrá-la para o formato novo. Não há como reabri-la.

**O que fazer:** **Importe** o backup que você tirou por **Exportar** — recupera a mesma chave e ninguém precisa reinstalar nada. Sem backup, a última saída é **Gerar nova chave** (veja acima, com a consequência para os clientes). O plugin nunca gera par novo por conta própria por cima de uma chave ilegível, justamente para não trocar a chave pública sem você saber.

**"A chave de assinatura ainda está protegida pelas chaves de segurança do wp-config.php…"** (aviso no wp-admin de que a chave ainda não foi migrada para o formato novo) — a pasta de uploads do WordPress não aceita escrita, então o plugin não conseguiu criar o arquivo da chave-mestra. Corrija a permissão de escrita da pasta de uploads e recarregue a página; até lá, uma troca das chaves de segurança do WordPress deixaria a chave ilegível.

**"nenhuma — assinatura indisponível"** em Fonte em uso — nenhuma das três fontes está configurada e a chave nunca chegou a ser gerada. Emissão de licença, validação e token de serviço ficam indisponíveis até isso ser corrigido; importe uma chave existente ou aguarde o plugin gerar uma sozinha na próxima operação que precisar dela.
