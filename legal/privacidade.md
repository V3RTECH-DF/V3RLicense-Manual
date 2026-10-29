---
title: Política de Privacidade
parent: Legal
nav_order: 1
---

# Política de Privacidade

**V3RLicense — Servidor de Licenças dos Plugins WordPress da V3RTECH e da RIT**

Versão 0.1 (minuta) — Agosto de 2026

---

{: .warning }
> **Minuta pendente de revisão do dono do produto.**
>
> Este documento foi produzido por adaptação da política do V3REvent e por
> levantamento direto do schema de dados do V3RLicense — não foi redigido
> nem revisado por quem responde juridicamente pelo produto. As bases legais
> propostas aqui são **sugestão fundamentada**, não decisão. Retenção,
> contato do titular e o tratamento do pedido de eliminação já foram
> decididos pelo dono do produto e estão refletidos abaixo; o que falta é
> só a revisão jurídica formal do texto.

---

## Quem é o controlador

{: .important }
> Diferente dos plugins que licencia, o **V3RLicense não é auto-hospedado
> pelo cliente**: ele roda em infraestrutura da própria V3RTECH
> (`v3rtech.com.br`) e é operado pela equipe V3RTECH/RIT. Por isso, aqui a
> **V3RTECH é a controladora** dos dados pessoais tratados por este sistema
> — não há um "controlador terceiro" para quem repassar essa
> responsabilidade, como acontece na política de cada plugin.

## O que este sistema trata, e por quê

| Dado | Onde fica | Origem | Finalidade proposta | Base legal proposta |
|---|---|---|---|---|
| Nome e e-mail de contato da organização cliente | Cadastro de clientes | Digitado por um operador ao emitir uma licença (ou editado depois) | Identificar a quem uma licença pertence, para emissão, renovação, revogação e comunicação sobre o serviço | **Execução de contrato ou procedimentos preliminares** (Art. 7º, V, LGPD) — a licença, paga ou concedida por isenção, é uma relação entre a V3RTECH/RIT e a organização cliente, e o contato é indispensável para administrá-la |
| Anotação livre em uma licença | Cadastro de licenças | Texto digitado pelo operador na emissão | Registro interno do motivo/contexto de uma licença (ex.: número de pedido, confirmação de filiação) | Mesma base do item acima — mas ver alerta abaixo |
| Domínio, versão do plugin/PHP/WordPress e datas de uso | Registro de ativações | Enviado automaticamente pelo plugin instalado no site do cliente, ao ativar/consultar a licença | Controlar quantos sites usam uma licença (cota de ativação) e apurar problema técnico | Ver discussão abaixo — depende de quem é o titular |

{: .warning }
> **A anotação livre da licença pode virar dado pessoal por descuido.** O
> campo existe para contexto operacional ("pedido #4821, boleto pago em
> 20/08"), mas nada impede alguém de colar ali um nome completo, um CPF ou
> outro dado sensível que não precisaria estar registrado. **Recomendação:**
> use a anotação só para o mínimo necessário à gestão da licença — número de
> pedido, data, motivo da origem — e nunca para dado de identificação
> pessoal que já não esteja no cadastro de cliente.

### O registro de ativação é dado pessoal?

Normalmente, não diretamente: um domínio de site pertence a uma organização, não a uma pessoa física identificável por ele. **Isso muda quando o cliente é uma pessoa física** (um profissional autônomo licenciando o plugin em nome próprio, por exemplo) — nesse caso, o domínio e o padrão de uso podem se tornar dado pessoal por associação ao nome/e-mail já cadastrado.

**Proposta de base legal para esse caso:** **legítimo interesse** (Art. 7º, IX, LGPD), pela necessidade operacional de controlar a cota contratada e de oferecer suporte técnico — sujeito ao teste de proporcionalidade e balanceamento que a LGPD exige para essa base, o que cabe à revisão jurídica confirmar.

## O vínculo com a conta de usuário do WordPress

O cadastro de cliente pode ser vinculado a um usuário do WordPress (a conta que o titular usa na loja). Esse vínculo **é usado**: é por ele que o cliente, logado, vê suas licenças na área "Minhas licenças", desativa um site e gerencia seus tokens de acesso a serviços, e que a compra pelo WooCommerce é associada ao cadastro. Em caso de anonimização (ver "Direitos do titular"), o vínculo é desfeito.

## Envio de e-mails e a terceiros

O sistema envia **e-mails transacionais** ao contato do cliente — o envio da chave de licença e os avisos de vencimento e renovação. O envio sai pelo **transporte de e-mail do WordPress do próprio site** da V3RTECH, e não por um serviço de e-mail contratado à parte pelo V3RLicense. O sistema guarda um **registro de cada envio**, com o destinatário, o resultado e, em caso de falha, o texto do erro; esse registro é dado pessoal e é limpo na anonimização do cliente.

Fora isso, o V3RLicense **não envia** os dados de cliente, licença ou ativação a nenhum serviço externo — não há webhook nem API de terceiro que os leve para fora do banco de dados do servidor.

## Retenção

O cadastro de cliente e o histórico de licença e de ativações são mantidos por **cinco anos após a revogação ou a expiração da licença**.

{: .warning }
> **Não existe expurgo automático.** Nenhuma rotina roda em segundo plano
> no V3RLicense para apagar registro nenhum — a eliminação ao fim do prazo
> de cinco anos é um **ato manual**, feito por alguém da equipe operadora.
> Não presuma que o prazo acima se cumpre sozinho: sem uma verificação
> periódica deliberada, um registro pode continuar existindo além do prazo
> simplesmente porque ninguém o removeu.

## Direitos do titular, e uma limitação real

O titular (a pessoa de contato cadastrada, ou o representante da organização) tem os direitos previstos na LGPD — confirmação, acesso, correção, eliminação, portabilidade, entre outros.

{: .important }
> **Exclusão de cliente (regra vigente desde a versão 0.38.1, de
> 29/10/2026).** Cliente que tem licença, em qualquer estado, **não é
> excluído**: a ação **Excluir** da tela de Clientes é recusada, nada é
> revogado nem apagado, e o caminho é **anonimizar** o cadastro. O
> **histórico das licenças é preservado** pela retenção de cinco anos
> descrita acima. Só cliente sem nenhuma licença pode ser excluído.

{: .important }
> **Eliminação de cliente com histórico de licença: anonimização (desde a
> versão 0.38.0, de 29/10/2026).** O cadastro de um cliente que tem
> licença vinculada não pode simplesmente sumir: o **histórico da
> licença** precisa sobreviver pelo prazo de retenção de cinco anos acima.
> O que precisa sobreviver é o histórico, não a **identificação da
> pessoa** por trás dele, e é isso que a tela de Clientes passa a oferecer
> com a ação **Anonimizar**.
>
> **O que a anonimização faz.** Troca o nome e o e-mail do cliente por
> marcadores ("Cliente anonimizado" seguido do número do cadastro, com
> e-mail inexistente), mantendo a linha do cadastro e as licenças
> vinculadas. Também apaga o destinatário e o texto de erro do registro de
> envio de e-mails, o nome que ficou gravado dentro dos tokens de acesso a
> serviços, e o vínculo do cadastro com a conta de usuário do WordPress.
> Do valor anterior o sistema guarda **apenas que a anonimização foi feita
> e quando** — nunca o nome ou o e-mail antigos. Depois dela, o cliente
> anonimizado não recebe licença nova nem reenvio da chave.
>
> **O que a anonimização não faz.** Não apaga o **usuário do WordPress**
> nem os **pedidos do WooCommerce** do titular, que pertencem a outros
> sistemas e têm seus próprios dados e prazos; a eliminação desses é
> tratada à parte, por quem os administra. Também não é desfazível: não há
> como recuperar o nome e o e-mail depois de anonimizar. E não há
> anonimização em lote — cada cliente é feito individualmente.
>
> **O campo de anotação livre da licença é escolha de quem opera.** Ele é
> texto digitado pelo operador e pode conter dado pessoal colado por
> descuido (ver alerta acima); uma rotina automática não consegue varrer
> texto livre com segurança. Por isso, ao anonimizar, a tela **mostra as
> anotações das licenças do cliente** e o operador escolhe **limpar ou
> manter** cada uma. Anotação mantida pode continuar identificando a
> pessoa, e conferir isso é responsabilidade humana. A anotação já gravada
> antes da anonimização continua sendo corrigida editando o texto da
> licença.
>
> A implementação está registrada em **[V3RLicense-Code#19 — Anonimizar
> cliente com licença vinculada](https://github.com/V3RTECH-DF/V3RLicense-Code/issues/19)**.

Correção, acesso e portabilidade dos dados de contato são atendidos manualmente pela equipe operadora, editando o cadastro em **[Cadastrar cliente](/processos/cadastrar-cliente/)**.

## Segurança

- O acesso ao painel administrativo do V3RLicense é restrito a quem tem capacidade de administração no WordPress que o hospeda.
- Tokens de publicação e a chave de assinatura das respostas do servidor não são dado pessoal, mas seguem prática equivalente de segredo — nunca expostos em log ou e-mail.

---

## Alterações nesta Política

Esta é uma minuta. A versão vigente, quando revisada e aprovada, estará disponível em [docs.v3rlicense.v3rtech.com.br/legal/privacidade](https://docs.v3rlicense.v3rtech.com.br/legal/privacidade/).

---

## Contato

- **DPO da V3RTECH:** [dpo@v3rtech.com.br](mailto:dpo@v3rtech.com.br)
- **Central de Privacidade da V3RTECH:** [v3rtech.com.br/central-de-privacidade](https://v3rtech.com.br/central-de-privacidade/) — canal para exercer os direitos do titular (acesso, correção, eliminação, portabilidade e demais previstos na LGPD).

---

*Versão 0.1 (minuta) — Agosto de 2026. Documento não revisado juridicamente; não substitui a assessoria jurídica que a V3RTECH deve buscar antes de publicar esta política como vigente.*
