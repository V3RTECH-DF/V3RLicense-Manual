---
title: "Diagnóstico: cliente diz que não atualiza"
parent: Como faço…
nav_order: 12
---

# Diagnóstico: cliente diz que não atualiza

## Por que isto importa

É a dúvida que mais chega — o cliente vê a versão nova anunciada, mas o wp-admin dele não mostra o aviso de atualização. Antes de mexer em qualquer cadastro, siga esta ordem: a causa mais provável está no topo.

## Roteiro de verificação

1. **A licença dele está ativa?** Abra **Licenças**, filtre pelo nome ou e-mail do cliente. Se o status for "Expirada" ou "Revogada", é isso — atualização e download são bloqueados enquanto a licença não estiver ativa (veja **[Como funciona a licença](/como-funciona/)**). A saída é **[renovar](/processos/renovar-licenca/)** (se expirada) ou emitir uma licença nova (se revogada).

2. **A licença cobre o produto certo?** Confira a coluna "Cobertura" na linha da licença. Cliente com licença que não cobre aquele plugin não recebe atualização dele — parece óbvio, mas é comum quando o cliente usa vários plugins da casa e confunde qual licença é qual, ou quando a licença cobre só parte do catálogo (produtos específicos, ou uma lista de acesso da qual esse plugin ainda não faz parte).

3. **A ativação do domínio dele está de pé?** Abra **Ver ativações** na licença e confirme que o domínio do cliente aparece com status "ativo", não "desativado". Se foi desativado por engano (veja **[Liberar uma ativação](/processos/liberar-ativacao/)**), o plugin perde a ativação — ele pode continuar funcionando, mas a validação falha. Já que você está nessa tela: se o número de ativações parecer maior do que deveria, olhe a coluna **"Ambiente de teste"** — linhas marcadas "sim" não contam na cota, então não são elas que estão ocupando a vaga do cliente.

4. **O release existe mesmo?** Abra **Releases**, selecione o produto, confirme que a versão que você acha que publicou está realmente lá e marcada como a mais recente (estrela). Um release removido por engano (veja **[Remover um release publicado](/processos/remover-release/)**) explica por que ninguém recebe o aviso.

5. **O PHP do site dele atende ao mínimo do produto?** Desde 27/08/2026, todos os plugins da casa exigem **PHP 8.2**. Se o site do cliente roda uma versão mais antiga, o WordPress **recusa a atualização em vez de instalar e quebrar o site** — mas não avisa o motivo em lugar nenhum visível: o aviso de atualização simplesmente não aparece, como se estivesse tudo em dia. É a causa mais fácil de passar batido, porque não gera nenhum erro para o cliente reportar. Peça para ele confirmar em **Ferramentas → Saúde do site → Informações**, no painel do WordPress dele. Se o PHP estiver abaixo do exigido, a saída é o cliente (ou a hospedagem dele) atualizar o PHP — não há nada a fazer daqui. Se, além de desatualizado, o plugin **já estiver ativo** nesse PHP insuficiente, ele se autodesativa sozinho e mostra ao administrador do site uma mensagem com o mínimo exigido e o instalado — o que também ajuda a confirmar o diagnóstico sem precisar pedir print de "Saúde do site".

6. **Chegou até aqui e nada bateu?** É hora de olhar o lado do cliente: confirme com ele que a chave de licença colada no plugin é exatamente a chave certa (sem espaço, sem caractere cortado), e que o domínio dele bate com o que está ativado aqui — um subdomínio (`www.` a mais ou a menos) pode contar como domínio diferente.

## Exemplo

Cliente reporta que o V3RHelp diz "nenhuma atualização disponível" mesmo sabendo que a versão `2.1.0` foi anunciada. Você confere: a licença dele está **ativa**, é do produto certo, a ativação do domínio está de pé. No passo 4, você descobre que a `2.1.0` foi publicada para o produto errado por engano (outro plugin com nome parecido) — a correção é remover o release do produto errado e publicar de novo no produto certo.

## Dicas e armadilhas

{: .tip }
> **Siga a ordem.** Os quatro primeiros passos cobrem a esmagadora maioria dos casos e são todos verificáveis sem sair do painel do V3RLicense — resolva por aqui antes de pedir print ou log ao cliente. O passo do PHP é o único que depende de uma informação do lado do cliente, mas vale confirmar cedo: é a causa mais silenciosa de todas.

- **Licença ativa não garante versão nova visível na hora** — o wp-admin do cliente consulta o servidor periodicamente (cache do próprio WordPress), não em tempo real. Se tudo aqui está correto, pode ser só uma questão de o cliente forçar a checagem de atualizações no painel dele.

## Quando dá errado

Se os seis passos não explicarem o caso, é hora de apoio técnico — pode ser um problema de rede entre o site do cliente e o servidor, não algo visível neste painel.

## Limites do papel

Sem papel intermediário — qualquer pessoa com acesso ao painel consegue seguir este roteiro até o fim.
