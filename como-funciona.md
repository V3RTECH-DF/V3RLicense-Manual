---
title: Como funciona a licença
nav_order: 3
---

# Como funciona a licença

Esta página é a **referência canônica** da política de licenciamento da V3RTECH e da RIT. Os manuais de cada plugin (V3REvent, V3RHelp, V3RLGPD, GE Associados, RIT360 Solidário, RIT360 Premiado…) apontam para cá quando o cliente final tem dúvida sobre a própria licença — é aqui, e só aqui, que a política vive por escrito.

## Por que isto importa

Quem opera o V3RLicense precisa entender a política com precisão para responder o cliente sem inventar, e para não prometer nem negar algo que o sistema não faz. É também o texto que você copia (ou linka) quando um cliente pergunta "por que perdi acesso?" ou "por que não perdi?".

## O que a licença dá direito

A licença de um plugin da V3RTECH/RIT dá direito a **atualização e correção** — não a uma funcionalidade extra dentro do plugin. Os plugins são distribuídos sob **GPL** (veja **[Licença de Uso do Software](/legal/licenca/)**), o que significa que o código já pertence a quem o instalou; o que se vende é o serviço de manter esse código atualizado.

Uma mesma chave de licença pode cobrir **mais de um plugin** — é o caso de organizações parceiras ou filiadas à RIT com direito ao catálogo inteiro. Nesse caso, a mesma chave é colada em cada um dos plugins cobertos. Status, expiração e renovação são da **licença como um todo** — vencer ou revogar afeta todos os plugins cobertos ao mesmo tempo. Só a cota de ativação é diferente: ela é contada **separadamente para cada plugin coberto** (veja a seção seguinte).

{: .important }
> **Licença vencida não desliga o plugin.** Quando uma licença expira ou é revogada, o plugin cliente **continua funcionando exatamente como antes** — nenhuma tela para de abrir, nenhum recurso é bloqueado. O que muda é que o plugin **para de receber atualização e correção** até a licença ser renovada.
>
> Isso é decisão de política, não limitação técnica: o endpoint que o plugin usa para saber o próprio status (`/validate`) sempre responde com sucesso, informando o status real (`active`, `expired`, `revoked`) — nunca nega a resposta por causa do status. Só os endpoints de atualização e download recusam quando a licença não está em dia, porque é exatamente isso que a licença cobre.

## A venda pela loja emite a licença sozinha

Um produto publicado na loja WooCommerce a partir da tela **[Venda do plugin](/modulos/venda-do-plugin/)** — seja pela seção de assinatura (combinações de duração e sites) ou pela seção de perpétua e negociada — não precisa de ninguém do lado do V3RLicense para virar licença: o pedido pago é que dispara tudo:

- **Compra avulsa** (produto de licença perpétua) — pedido pago emite **uma licença por unidade comprada**, e o V3RLicense manda ao cliente **um e-mail só**, com todas as chaves, cada uma identificada pelo produto correspondente. Comprou 5, o cliente recebe 1 e-mail com as 5 chaves. Comprar uma unidade continua igual, num e-mail com uma chave.
- **Assinatura** (produto de licença mensal, trimestral, semestral ou anual) — o pagamento inicial emite a licença do mesmo jeito; cada cobrança de renovação seguinte **estende essa mesma licença** — mesma chave, mesmas ativações preservadas — em vez de criar uma segunda. O cliente não reconfigura nada a cada cobrança, e a renovação automática não manda e-mail (o próprio WooCommerce já confirma a cobrança).

Em ambos os casos o cliente é sempre identificado pela **conta com que fez o pedido** na loja, nunca por um e-mail digitado à parte.

{: .note }
> **Um pedido com item avulso e item de assinatura gera dois e-mails, não um.** Compra avulsa e assinatura são emitidas em momentos diferentes do processamento do pedido — misturar os dois tipos no mesmo carrinho não é defeito, é o motivo de chegarem separados.

## Os cinco status de uma licença

| Status | O que significa | O que o plugin cliente sente |
|---|---|---|
| **Ativa** | dentro da validade, não revogada | atualização normal |
| **Em carência** | venceu, mas dentro dos 15 dias seguintes ao vencimento — só para licença que **gera cobrança** | atualização normal, como se ainda estivesse ativa |
| **Suspensa por falta de pagamento** | venceu e passou dos 15 dias de carência, sem renovar — só para licença que gera cobrança | plugin funciona; atualização e download bloqueados até renovar |
| **Expirada** | venceu e a origem **não gera cobrança** (licença concedida) — vai direto para expirada, sem carência | plugin funciona; atualização e download bloqueados até renovar |
| **Revogada** | cancelada manualmente (reembolso total, fraude, decisão da casa) | plugin funciona; atualização e download bloqueados até nova decisão |

{: .note }
> **Revogação é decisão que só se desfaz emitindo outra coisa.** A tela de Licenças não tem um botão de "reverter revogação" — uma licença revogada permanece revogada. Se o motivo da revogação deixar de existir, a saída é **[emitir uma licença nova](/processos/emitir-licenca/)** ou, quando fizer sentido, ajustar o cadastro manualmente com apoio técnico.

## Carência e suspensão — só para quem paga

![Lista de licenças mostrando os cinco status lado a lado: Ativa, Suspensa por falta de pagamento, Revogada, Expirada e Em carência](/assets/screenshots/licencas-status-novos.png)

Uma licença vencida não vira "suspensa" automaticamente — o que acontece depende de a **origem** dela [gerar cobrança ou não](/modulos/origens/):

- **Origem que gera cobrança** (ex.: "Venda (WooCommerce)") — a licença vencida entra em **carência por 15 dias corridos**, contados do vencimento. Durante a carência, o plugin do cliente continua recebendo atualização normalmente, como se a licença estivesse ativa. Passados os 15 dias sem renovar, a licença vira **suspensa por falta de pagamento**.
- **Origem que não gera cobrança** (ex.: "Isenção — filiada à RIT") — vence e vira **expirada** direto, sem carência nenhuma. Faz sentido: não há cobrança pendente para dar tempo de regularizar.

{: .important }
> **Suspensa não derruba nada no site do cliente.** É a mesma regra de sempre para licença sem cobertura: o plugin já instalado continua funcionando normalmente — só para de receber novas versões e correções. `activate`/`validate` continuam liberados; só atualização e download ficam bloqueados.

Regularizar o pagamento — pela renovação manual, pela [renovação em lote](/processos/renovar-licenca/), ou pela cobrança automática de uma assinatura — devolve a licença a "Ativa" na hora, porque o status é sempre recalculado a partir da data de vencimento, nunca depende de um processo agendado ter rodado.

### Estorno

O WooCommerce dispara o mesmo evento para estorno total e parcial; o que diferencia um do outro é o pedido ter ficado **inteiramente** reembolsado ou não:

- **Estorno total** — revoga a licença.
- **Estorno parcial** — não mexe na licença. Um desconto ou ajuste parcial no pedido não tira a cobertura do cliente.

Cancelamento de assinatura, por si só, **não revoga nada**: o cliente mantém o acesso normal até o fim do período que já foi pago.

## Avisos automáticos por e-mail

O V3RLicense avisa por conta própria, sem que o operador precise lembrar de nada. A régua muda conforme o tipo de cobrança da licença:

**Antes do vencimento**, ao cliente de uma licença comprada:

| Tipo de licença | Antecedência dos avisos |
|---|---|
| Mensal | 7 e 1 dia antes |
| Trimestral | 15, 7 e 1 dia antes |
| Semestral e Anual | 30, 15, 7 e 1 dia antes |
| Vitalícia/Perpétua | nenhum aviso — nunca vence |

**Assinatura recorrente ativa** foge dessa régua: o cliente recebe **um aviso só**, sempre 7 dias antes da cobrança automática — a régua completa faria pouco sentido para quem paga sozinho, sem precisar agir.

**Durante a carência** (só licença que gera cobrança), o cliente recebe mais avisos: um no dia em que a carência começa, um quando faltam 8 dias para a suspensão, um no último dia do prazo, e um quando a suspensão de fato acontece.

**Licença concedida** segue outra regra por completo: **quem é avisado é o operador, nunca o cliente**, porque a renovação dessas licenças é sempre manual. O e-mail vai para o endereço cadastrado em **[Configurações](/modulos/configuracoes/)**, na mesma antecedência da tabela acima, e sugere usar a renovação em lote.

{: .note }
> **A régua roda mesmo sem loja.** Ela usa o agendador do próprio WordPress, não o mecanismo do WooCommerce — continua funcionando mesmo para licença vendida fora da loja (sem pedido vinculado) ou se a loja for desativada. O que decide se uma licença entra na régua é a origem estar marcada como "gera cobrança", nunca a existência de um pedido.

### Identidade visual e remetente

Desde a v0.13.1, todo e-mail que o cliente recebe — chave da licença, avisos de vencimento e de carência, e o aviso ao operador de uma licença concedida — usa a identidade visual institucional da V3RTECH: logomarca no cabeçalho, títulos em verde escuro, e a chave da licença destacada num bloco amarelo para não passar despercebida no meio do texto. O conteúdo e o comportamento continuam os mesmos de sempre — só a aparência mudou.

Os e-mails que o **WooCommerce** manda por conta própria (confirmação de pedido, recibo, ao cliente que compra pela loja) ganharam a mesma identidade, para o cliente não notar dois visuais diferentes numa mesma compra.

**Isso também mudou para quem opera:** os avisos que o WooCommerce manda ao **administrador da loja** — novo pedido, pedido cancelado, pedido malsucedido, gateway de pagamento ativado, e os seis avisos de assinatura (nova cobrança de renovação, assinatura trocada, cancelada, expirada, suspensa e reativada) — passaram a ir para `comercial@v3rtech.com.br`. Antes, quatro desses avisos iam para `suporte@v3rtech.com.br` por configuração explícita, e os outros seis caíam lá por herdarem o e-mail de administração do WordPress (que continua sendo `suporte@`). **Quem acompanhava pedido novo pela caixa do suporte precisa passar a olhar `comercial@`.** O remetente dos e-mails da loja também passou a ser `comercial@v3rtech.com.br`, no lugar de `suporte@`.

{: .important }
> Os e-mails que o **V3RLicense** manda diretamente (chave, vencimento, carência, aviso ao operador de isenção) já saíam como `V3RTECH <comercial@v3rtech.com.br>`, e continuam assim — o remetente deles é definido pelo próprio plugin, não pela configuração da loja nem pelo padrão do WordPress. O que mudou de remetente foram os e-mails nativos da **loja WooCommerce**, que agora saem do mesmo endereço.

## Ativação por domínio, e a cota

Cada site (domínio) em que o cliente ativa um plugin conta como **uma ativação**, com um limite (`activations_max`) — quando o produto não define um padrão, é ilimitado. Para uma licença que cobre mais de um plugin, esse limite é **contado separadamente para cada plugin**: ativar o V3RLGPD num domínio não usa a cota do V3RHelp! coberto pela mesma chave.

{: .tip }
> **Ambientes de teste não consomem cota.** O servidor reconhece automaticamente quando uma ativação vem de um ambiente de desenvolvimento ou homologação (por padrões do próprio domínio) e não soma essa ativação ao limite da licença. Isso existe para o cliente poder testar o plugin num site de staging sem gastar a cota da licença de produção — se você olhar a lista de ativações de uma licença e ver mais linhas do que o limite contratado, é provável que algumas sejam de teste (a coluna "Ambiente de teste" mostra isso). Os critérios exatos de reconhecimento não são públicos — não são um dado que o manual expõe.

Quando o cliente muda de domínio (staging virou produção, ou o site mudou de endereço) e a licença está no limite, é preciso **[liberar uma ativação](/processos/liberar-ativacao/)** antes de ele conseguir ativar no domínio novo.

## Renovação

Renovar uma licença expirada **reativa a mesma chave** — o cliente não recebe uma chave nova, e as ativações que ele já tinha continuam valendo, sem precisar reativar nada. Veja o passo a passo em **[Renovar uma licença](/processos/renovar-licenca/)**.

## A aba "Minhas licenças", na conta do cliente

Desde a v0.14.0, o cliente tem uma aba própria — **"Minhas licenças"**, dentro de "Minha conta" no site — onde vê e resolve sozinho boa parte do que antes só o suporte podia dizer. Isso muda o que chega até você: "perdi a chave", "até quando vale" e "quantos sites ainda posso usar" deixam de ser chamado.

### O que o cliente vê

Para cada licença dele — comprada, concedida por parceria ou por isenção, tanto faz: a aba mostra as licenças da **pessoa**, não as compras dela —, o cliente vê o produto coberto, a chave inteira (sem máscara), até quando vale e quanto falta, o estado, e em quais sites está ativada com quantas ativações ainda cabem. **Quando uma licença cobre mais de um produto, a cota aparece separada por produto**, nunca somada — a mesma regra de sempre, só que agora visível para ele também.

### O cliente desativa um site sozinho

O cliente pode desativar um domínio direto por ali. É a **mesma operação** que você faz em **[Liberar uma ativação](/processos/liberar-ativacao/)** — não existe um caminho de desativação paralelo, o plugin cliente e a aba usam o mesmo mecanismo por baixo. Desativar libera a vaga e **não mexe na validade**: quem desativa não perde tempo pago nem ganha tempo. O site desativado para de receber atualização e correção; a licença continua valendo e pode ser ativada em outro lugar, ou nele mesmo de novo.

Consequência prática: "troquei de domínio" e "estourei a cota" deixam de exigir sua intervenção na maior parte dos casos.

### Troca de plano, pela própria assinatura

Desde a v0.19.0, o cliente com assinatura ativa (produto vendido pela seção de assinatura de **[Venda do plugin](/modulos/venda-do-plugin/)**, com combinações de duração e sites) pode trocar de combinação direto na própria assinatura, pelo mecanismo nativo do WooCommerce Subscriptions — subir para mais sites, mudar a periodicidade, ou descer. A licença acompanha a troca automaticamente: número de ativações e tipo passam a ser os da combinação nova, **mantendo a mesma chave e os sites já ativos**.

{: .important }
> **Descer de plano não tem multa nem custo adicional.** A cobrança menor passa a valer normalmente a partir da própria troca — o preço em si é assunto do WooCommerce Subscriptions; o V3RLicense só decide se a **cobertura** cabe (próxima seção).

#### Descer de plano com mais sites ativos do que o novo permite é recusado

Se o cliente tenta descer para uma combinação com um limite de sites menor do que ele tem **ativado hoje** (contando só ativações que não são de ambiente de teste — a mesma regra de sempre), a troca é **barrada antes de entrar no carrinho**. Ele vê uma mensagem dizendo **quantos sites precisa desativar**, com um link direto para a aba **"Minhas licenças"**, onde ele mesmo desativa (veja a seção anterior).

{: .warning }
> **O sistema nunca desativa site por conta própria.** Foi decisão de produto deliberada — desativar um site em produção sem a pessoa escolher qual derrubaria a atualização dele sem aviso. A saída é sempre o cliente decidir e agir, nunca automática.

Consequência prática para o suporte: **"quero mais sites" e "quero pagar menos" deixam de ser chamado** — o cliente troca sozinho. O chamado que sobra é **"não consigo descer de plano"**, e a resposta é a própria mensagem que a tela já mostra: desativar o excedente na aba "Minhas licenças" primeiro.

### Licença sem valer mostra o caminho de volta

Quando a licença não está em dia, a aba oferece o caminho de regularizar — e o caminho depende da **situação real**, não só do rótulo do status:

| Situação | Para onde a aba leva |
|---|---|
| Em carência ou suspensa, com cobrança em aberto | Aba "Assinaturas" — o cliente já paga ali |
| Vencida, com assinatura encerrada | Reassinar (mecanismo nativo do WooCommerce Subscriptions) |
| Vencida, sem assinatura (compra avulsa) | Comprar de novo o mesmo produto |

{: .note }
> **A cobrança nova conta a partir da data em que a pessoa volta a pagar, nunca da validade anterior.** Quem ficou seis meses sem renovar não paga por um período que não usou — é a mesma lógica de sempre (veja **[Renovar uma licença](/processos/renovar-licenca/)**), só que agora é o próprio cliente quem inicia. Essa é uma resposta frequente de suporte; vale ter decorada.

Se o produto original da licença **saiu de venda ou foi despublicado**, a aba não vira um link quebrado: ela oferece a **[página de produtos disponíveis](/modulos/configuracoes/)** configurada pelo gestor (quando houver) e o contato. Sem essa configuração preenchida, o cliente vê só o contato.

### Armadilha de suporte — o nome do estado não é o mesmo dos dois lados

{: .important }
> **O painel e o cliente usam palavras diferentes para o mesmo estado, de propósito.** Onde você vê "Expirada", "Suspensa por falta de pagamento" e "Em carência", o cliente vê **"Vencida"** nos dois primeiros e **"Vencida — renovação em aberto"** no terceiro. A distinção entre esses três estados é operacional — importa para você decidir cobrança —, mas o texto do painel acusaria de calote quem talvez só tenha decidido não renovar.

Se você abrir a tela do cliente por cima do ombro dele (ou olhar um print que ele mandou) esperando ver a mesma palavra do painel, vai estranhar. Não é bug: é a mesma licença, vista com vocabulário diferente para cada lado. (Até a v0.16.0 essa distinção vazava — uma licença simplesmente vencida chegou a aparecer como "Suspensa por falta de pagamento" para o cliente; corrigido na v0.16.1.)

## Token de acesso a serviço da casa

Desde a v0.30.0, uma licença pode dar acesso a mais do que atualização de plugin: ela pode dar acesso a um **serviço da casa** — hoje, o **V3RSigner**, o serviço que assina PDF. Quando isso acontece, o cliente recebe, além da chave de licença, um **token**: uma cadeia de texto longa que ele mesmo cola no sistema que vai consumir o serviço (por exemplo, no lugar onde o site dele integra com o V3RSigner).

{: .note }
> **Nem toda licença tem token.** Só quando o produto comprado está ligado a um serviço (cadastro que o operador faz em **[Audiências de serviço](/modulos/audiencias-de-servico/)**). A imensa maioria das licenças — que só cobrem plugin — nunca mostra esse bloco.

### O que o cliente vê

Na aba "Minhas licenças", a licença que tem token mostra um bloco próprio, logo abaixo da tabela de produtos:

![Bloco "Token de acesso a serviço da casa" na aba Minhas licenças, com o token em claro, um botão Copiar, a validade e a frase descrevendo a trava atual](/assets/screenshots/minhas-licencas-token-servico.png)

- **O token em claro**, com um botão **Copiar** — sempre visível, sempre disponível. Isso é diferente do e-mail de chave de licença, que é enviado uma vez: aqui, o cliente pode voltar a essa aba a qualquer momento e copiar o token de novo, sem precisar guardar o e-mail original nem pedir para o suporte reenviar.
- **Válido até:** a data (e hora) em que o token deixa de valer, ou "não expira" para os poucos casos sem prazo.
- **A trava atual**, sempre escrita por extenso — nunca em silêncio, nem quando não há trava nenhuma.

### A trava do token — o que muda a segurança de quem compra

A trava decide **quem** consegue usar o token, além de quem tem o valor dele em mãos:

- **Sem trava** — é como todo token **nasce**. Quem estiver com a cadeia de texto pode assinar em nome do cliente, de qualquer lugar, sem mais nenhuma verificação. É simples de configurar (não exige nada do cliente) e é adequado para um primeiro teste, mas não protege contra o token vazar — por e-mail encaminhado à toa, por exemplo, ou por um arquivo de configuração commitado por engano.
- **Com trava por certificado** — o token só funciona **junto** de um certificado que o cliente informou. Vazou o token sozinho? De nada serve a quem não tiver também o certificado correspondente. É a opção que recomendamos para qualquer uso além de teste.

{: .tip }
> **Mais de um certificado ao mesmo tempo, de propósito.** O cliente pode cadastrar mais de uma impressão digital de certificado na mesma trava. Isso existe para a **renovação de certificado nunca virar um corte seco**: quando o certificado antigo está para vencer, o cliente cadastra o novo **antes**, o token passa a aceitar os dois, e só depois de confirmar que tudo funciona com o novo ele remove o antigo da lista. Sem essa sobreposição, trocar de certificado significaria um intervalo em que nada assina.

### Impressão digital do certificado

O "identificador" de um certificado, para efeito da trava — um resumo curto e único calculado a partir do certificado inteiro. Dois certificados diferentes nunca têm a mesma impressão digital; o mesmo certificado sempre calcula a mesma. É esse valor que o cliente cola no campo de certificados aceitos, nunca o arquivo do certificado em si.

### Reemitir e revogar — e por que não é instantâneo

O cliente tem dois botões, além de configurar a trava:

- **Reemitir** — gera um token novo com a trava atual, sem mudar mais nada. Útil quando ele suspeita que o token vazou, mas quer manter a mesma trava.
- **Revogar** — cancela o token, sem emitir outro no lugar.

{: .important }
> **Nem reemitir nem revogar cortam o acesso na hora.** O token anterior deixa de ser aceito em **até 1 hora**. Isso acontece porque quem confere o token do lado do serviço (o V3RSigner) não consulta o V3RLicense a cada uso — ele guarda uma lista de tokens cancelados e a atualiza periodicamente, para continuar funcionando mesmo se o V3RLicense estiver fora do ar num momento qualquer. É essa mesma lista que leva até 1 hora para refletir a revogação.
>
> **O que fazer nesse intervalo:** se o motivo for suspeita de vazamento, o cliente deve trocar o valor do token no sistema que o usa **assim que reemitir ou revogar** — não esperar a hora passar para agir. O token antigo continuar tecnicamente aceito por mais alguns minutos não é um bug a reportar; é a mecânica de propagação, e o passo seguro é sempre trocar o valor primeiro.

### Validade do token, e o que a renovação da licença muda

A validade do token é calculada **uma vez, na emissão** — não é recalculada sozinha depois:

- Licença com data de vencimento: o token vale até essa data mais os mesmos 15 dias de carência da própria licença.
- Licença perpétua (sem vencimento): o token vale 12 meses a partir de quando foi emitido.
- Em qualquer um dos dois casos, o token nunca passa de **13 meses a partir da emissão** — é um teto de segurança, para limitar o estrago de um token que vaze e nunca seja revogado.

{: .warning }
> **Renovar a licença não estende sozinho o token já emitido.** A data de "Válido até" do token não acompanha automaticamente a nova validade da licença renovada — ela fica congelada no que foi calculado quando o token nasceu. Se o cliente perceber que o token está perto de vencer, mas a licença está em dia, a saída é **Reemitir**: o botão gera um token novo, já calculado com a validade atual da licença. Avise o cliente disso quando ele perguntar "minha licença está ativa, por que o token venceu?" — a resposta é reemitir, não esperar.

### O que acontece se a licença deixar de valer

O token segue o destino da licença, com uma exceção:

| Situação da licença | O que acontece com o token |
|---|---|
| Em carência (venceu, dentro dos 15 dias) | **Continua funcionando normalmente** — carência nunca revoga token, a mesma regra de sempre para atualização de plugin. |
| Suspensa por falta de pagamento, expirada ou revogada | Entra na lista de cancelados automaticamente, dentro de até 1 hora — sem precisar de nenhuma ação do cliente ou do operador. |

Isso significa que **deixar de pagar não corta o acesso no mesmo dia**: o cliente tem os 15 dias de carência de sempre para regularizar, e só depois disso o token para de funcionar.

### Glossário desta seção

**Token de acesso a serviço da casa**
: A cadeia de texto que o cliente cola no sistema que consome um serviço da casa (ex.: V3RSigner). Diferente da chave de licença, aparece em claro na conta a qualquer momento — não é "mostrado uma vez só".

**Trava** (do token)
: A regra que decide quem, além de ter o valor do token, consegue usá-lo. Hoje só há a opção "sem trava" e "com certificado" pela conta do cliente.

**Impressão digital** (do certificado)
: Resumo curto e único calculado a partir de um certificado inteiro — é o que identifica o certificado dentro da trava, sem precisar do arquivo completo.

## Isenção para organizações filiadas à RIT

Organizações do terceiro setor filiadas à RIT recebem licença **gratuita** — sem passar por venda. Hoje isso é feito emitindo a licença pela origem "Isenção — filiada à RIT", com validade normalmente anual, **renovada manualmente** pela mesma tela de renovação. Não existe hoje verificação automática contra uma fonte externa de filiação — está registrado como funcionalidade futura (V3RLicense-Code#4). Veja o passo a passo em **[Emitir uma isenção](/processos/emitir-isencao/)**.

## Publicação de atualização

Quando uma versão nova de um plugin é publicada no V3RLicense, todo cliente com licença **ativa** daquele produto passa a ver o aviso de atualização no próprio wp-admin, do mesmo jeito que veria para um plugin do repositório oficial do WordPress. Cliente com licença expirada ou revogada não vê a atualização — mesmo que o plugin continue funcionando. Veja **[Publicar uma versão](/processos/publicar-uma-versao/)**.

## Glossário

**Ativação**
: Um domínio em que o cliente instalou e ativou o plugin com uma chave de licença. Conta contra a cota da licença, salvo ambiente de teste.

**Chave de licença** (`license_key`)
: O código que o cliente cola no campo de licença do plugin. Não muda ao longo da vida da licença — nem em renovação, nem em troca de plano.

**Combinação**
: Um par duração (tipo de licença) × número de sites, com preço próprio, cadastrado na seção de assinatura de **[Venda do plugin](/modulos/venda-do-plugin/)** — cada combinação vira uma variação do produto único na loja.

**Origem**
: O motivo de uma licença existir (venda, cortesia, isenção RIT…). Cadastro livre, sem regra de negócio própria — é rótulo, não lógica.

**Tipo de licença**
: A periodicidade (mensal, anual, perpétua…) usada para calcular a data de expiração na emissão e na renovação.

**Token de acesso a serviço da casa**
: A cadeia de texto que dá acesso a um serviço da casa (ex.: V3RSigner) ligado ao produto da licença — veja **[Token de acesso a serviço da casa](#token-de-acesso-a-serviço-da-casa)**, acima. Não confundir com o token de publicação, abaixo.

**Token de publicação**
: Credencial de máquina que publica release por API, sem passar pela tela — usada por pipeline de CI. Veja **[Gerenciar tokens de publicação](/processos/gerenciar-tokens-publicacao/)**.
