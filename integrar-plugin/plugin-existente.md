---
title: Integrar um plugin existente
parent: Preparar um plugin para o V3RLicense
nav_order: 2
---

# Integrar um plugin existente

## Por que isto importa

Um plugin que já roda em produção tem usuários reais, um `build-zip.sh` com convenções próprias e, às vezes, decisões antigas que colidem com o que o `v3r-core` espera — autoload incondicional, capability hardcoded, um filtro `user_has_cap` já registrado para outra coisa. Integrar aqui não é seguir a receita do zero (**[Plugin novo, do zero](/integrar-plugin/plugin-novo/)**) do início ao fim; é aplicá-la em cima do que já existe, com atenção redobrada nos pontos em que o legado diverge.

## 1. Levante o terreno antes de mexer

Antes do primeiro commit, confira quatro coisas no plugin como ele está hoje:

1. **PHP mínimo declarado** — se for menor que 8.2, decida se sobe agora (bloqueante para integrar) ou se a integração espera o bump acontecer numa entrega própria. Não misture os dois numa mesma PR sem dizer isso explicitamente na descrição.
2. **O plugin já usa Composer?** Se não, este é o primeiro pacote a introduzi-lo — os itens 2–4 da trilha do zero valem sem atalho.
3. **Existe algum filtro `user_has_cap` já registrado** para outra finalidade (RBAC próprio, outra integração)? Se sim, ele **não pode** ser substituído pelo do `v3r-core` — os dois convivem; o do `v3r-core` é registrado pela própria biblioteca (item 3) e só intercepta as duas capabilities de licença.
4. **O plugin carrega `vendor/autoload.php` incondicionalmente?** Se sim, isso precisa mudar — nenhum ponto do plugin pode depender de o Composer estar presente em runtime (ver item 3).

## 2. Declare a dependência e configure o Strauss

Mesmos passos 2 e 3 da trilha do zero: `v3rtech/v3r-core` em `require-dev` com o repositório `vcs`, bloco `extra.strauss` com namespace único do plugin, Strauss como `.phar` standalone.

{: .warning }
> **Se o plugin já usa Strauss para outra dependência**, o bloco `extra.strauss` já existe — você só acrescenta `"v3rtech/v3r-core"` ao array `packages` e o `override_autoload` do `plugin-update-checker` (ver trilha do zero, item 3). Não crie um segundo bloco `extra.strauss`: o Strauss lê um só, e o namespace/prefixos continuam sendo os que o plugin já usa para as outras dependências prefixadas.

## 3. Adapte o arranque do plugin

Envolva a instanciação do `Bootstrap` em `class_exists()`, exatamente como na trilha do zero (item 4) — mesmo que hoje o plugin sempre tenha o `vendor/autoload.php` disponível, o comportamento de produção (`vendor-prefixed/` gerado só depois de `composer run prefix`) é o mesmo para todo mundo.

{: .important }
> **Se o plugin já tinha um filtro `user_has_cap` próprio do licenciamento anterior a este** (por exemplo, uma integração feita antes da v0.4.0 do `v3r-core`, quando a biblioteca ainda exigia que o plugin registrasse o filtro), **remova-o**. Desde a v0.4.0, quem registra `user_has_cap` para as capabilities de licença é a própria biblioteca (`Bootstrap::withCapabilityDecider()`), com a guarda de saída antecipada embutida. Manter os dois filtros registrados ao mesmo tempo não é redundância inofensiva — é o cenário exato que já derrubou um site: um filtro sem a guarda correta, chamado numa ordem que reintroduz o ciclo `user_has_cap → user_can → user_has_cap`.

## 4. A tela de licença

Se o plugin já tem uma tela de configurações com abas, a integração mais natural é **uma aba nova**, não a tela padrão da biblioteca — consuma os quatro endpoints REST internos, com a capability de cada operação vinda do RBAC que o plugin já tem.

{: .warning }
> **Rótulo genérico é uma armadilha conhecida.** A tela padrão da biblioteca, sem `withProductName()`, se intitula só "Licença" — sem dizer de qual produto. Num site com mais de um plugin da casa instalado, essa entrada genérica é indistinguível das outras. Se optar pela tela padrão mesmo assim, **sempre** chame `withProductName()`.

## 5. Configuração de produção

Mesma regra da trilha do zero (item 6): as constantes compartilhadas `V3R_LICENSE_API_URL`/`V3R_LICENSE_PUBLIC_KEY` nunca são definidas pelo plugin, e os defaults de produção vão em constantes de nome próprio.

{: .important }
> **Se o plugin já tem alguma constante de configuração remota com nome parecido** (de uma integração anterior, ou de outro serviço), confira que ela não colide por engano com os dois nomes compartilhados. E se este plugin for o **segundo** da casa a integrar num site que já tem outro plugin licenciado — o caso mais comum na prática —, é justamente aqui que o guard "as duas vieram, ou nenhuma" precisa estar certo: um `define()` condicional mal escrito no primeiro plugin a carregar contamina o segundo (ver detalhe completo na trilha do zero, item 6).

## 6. Ajuste o `build-zip.sh` existente

O seu script de build já existe e tem uma ordem própria. Os pontos que **precisam** ser conferidos, não assumidos:

- O `cp -r vendor-prefixed` acontece **antes** de qualquer `dump-autoload` que o script rode dentro do diretório temporário do pacote — se o script achatar o layout (`src/includes/` virando `includes/`, por exemplo) e reescrever `composer.json` lá dentro, a ordem errada quebra com "`Could not scan for classes inside "vendor-prefixed/"`", no meio do build.
- `composer install` roda de novo, logo antes de cada `composer prefix` — nunca reaproveite o `vendor/` de uma execução anterior (ver a armadilha do `delete_vendor_packages` na trilha do zero, item 7).
- O guard de duas pontas (trilha do zero, item 8) entra como passo novo, se ainda não existir.

## 7. CI

Se o plugin já tem `ci.yml`, confira a matriz de PHP — ela precisa cobrir `['8.2', '8.3', '8.4']`, e não uma versão mais antiga que o `v3r-core` não suporta. Se o plugin ainda não tem `release.yml` disparado por tag, este é o momento de criar um — a publicação manual, sem pipeline, é aceitável só como fallback comprovado (não como rotina).

## 8. Cadastro e primeira publicação

- Confira que o produto já existe no painel do V3RLicense com o **slug exatamente igual** à pasta raiz do zip que o plugin gera hoje. Se o plugin nunca foi distribuído como zip com pasta nomeada por slug, esse é o momento de acertar isso — não depois.
- Gere um token de publicação escopado a este produto (**[Gerenciar tokens de publicação](/processos/gerenciar-tokens-publicacao/)**) e configure o secret `V3RLICENSE_PUBLISH_TOKEN` no repositório.
- **Faça a primeira publicação de teste manualmente**, pela pipeline, antes de considerar a integração concluída — não assuma que passou só porque a suíte automatizada ficou verde. A suíte não confere que o zip final tem a lib prefixada de verdade (ver o guard de duas pontas); só uma publicação real, seguida de conferência no painel, prova isso.

## Dicas e armadilhas específicas de migração

- **Trabalhar na lib e no plugin ao mesmo tempo, sem publicar tag a cada mudança:** adicione temporariamente um repositório `path` no `composer.json` do plugin, **antes** do `vcs` na lista (o Composer respeita a ordem), apontando para o checkout local do `V3RCore-Code`, com `"options": { "symlink": true }`. Nunca comite esse bloco — remova antes do PR e rode `composer update v3rtech/v3r-core` para voltar à versão travada.
- **`class_exists()` que só existia por acaso.** Um plugin com arranque já defensivo (por outro motivo — Composer sempre foi opcional em runtime, por exemplo) pode parecer já pronto para o item 3. Confira mesmo assim: "já era defensivo" e "está protegido no ponto certo, contra a ausência certa" não são a mesma garantia.
- **`LicenseManager` chamado fora do endpoint REST precisa de `try/catch`.** O controller REST já captura a exceção e devolve o código do contrato; uma rotina de diagnóstico ou comando WP-CLI próprio que chame o `LicenseManager` direto recebe a exceção propagada — tela branca, se ninguém capturar.

## Checklist antes de abrir o PR

- [ ] PHP mínimo do plugin já é 8.2, ou o bump está explicitamente escopado nesta mesma PR (não implícito).
- [ ] Nenhum filtro `user_has_cap` duplicado ou conflitante — o antigo (se existia) foi removido.
- [ ] Todo ponto que toque o `v3r-core` está atrás de `class_exists()` — inclusive onde o plugin já parecia defensivo.
- [ ] Tela de licença existe e identifica o produto (`withProductName()`, se for a tela padrão).
- [ ] `V3R_LICENSE_API_URL`/`V3R_LICENSE_PUBLIC_KEY` não são definidas pelo plugin, mesmo que outro plugin da casa já esteja no mesmo site de teste.
- [ ] `build-zip.sh` existente ajustado na ordem certa (cópia antes do dump-autoload do pacote) e reinstalando antes de cada prefixação.
- [ ] Guard de duas pontas presente no build ou na CI.
- [ ] Produto cadastrado com slug igual à pasta raiz do zip; token de publicação escopado gerado.
- [ ] Uma publicação de teste real foi feita e conferida no painel — não só a suíte verde.
- [ ] Testado com usuário **autenticado**, não só com requisição anônima.
