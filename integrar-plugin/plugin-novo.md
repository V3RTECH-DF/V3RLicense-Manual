---
title: Plugin novo, do zero
parent: Preparar um plugin para o V3RLicense
nav_order: 1
---

# Plugin novo, do zero

## Por que isto importa

Integrar desde o primeiro commit custa uma fração de integrar depois. Um plugin que nasce sem pensar em licenciamento tipicamente acumula decisões incompatíveis — autoload incondicional, capability hardcoded, constantes com nome genérico — que só aparecem como retrabalho quando alguém tenta encaixar o `v3r-core` mais tarde. Esta página é o que não pode faltar desde o início.

## 1. PHP mínimo: 8.2, em três lugares

O `v3r-core` exige `php: >=8.2`. Isso precisa aparecer em **três** lugares do seu plugin, não só um:

```json
{
    "require": { "php": ">=8.2" },
    "config": { "platform": { "php": "8.2" } }
}
```

E no cabeçalho do arquivo `.php` principal do plugin:

```php
/**
 * Plugin Name: Meu Plugin
 * Requires PHP: 8.2
 */
```

{: .important }
> **É o cabeçalho `Requires PHP`, não o `composer.json`, que faz o WordPress recusar instalação ou atualização num site incompatível.** O `composer.json` só importa no seu ambiente de build (dev, CI) — ele nunca viaja para o site do cliente nem é lido pelo WordPress. Sem o cabeçalho certo, um site em PHP 7.4 instala o plugin normalmente e só descobre a incompatibilidade num fatal error de sintaxe na ativação — ou pior, num ponto qualquer do código que só aquele PHP mais velho não entende.

{: .warning }
> **Um guard de versão de PHP escrito em sintaxe do PHP 8 não roda no PHP antigo que ele deveria barrar.** Se você quiser um aviso amigável em vez do fatal error de parse (recomendado — é isso que o cabeçalho `Requires PHP` sozinho não garante em toda instalação, dependendo de como o WordPress hospedeiro dispara a checagem), o arquivo que faz essa checagem precisa ser o único do plugin escrito em sintaxe válida desde o **PHP 7.0**: sem promoção de propriedade no construtor, sem tipos union, sem `match`, sem propriedades tipadas, sem operador nullsafe. Um `version_compare()` simples, sem classe, carregado por `require_once` antes de qualquer autoload — é o único jeito de mostrar "seu PHP é antigo demais" em vez de um erro que não diz nada disso.

## 2. Declare o `v3r-core` como dependência

```json
{
    "require-dev": {
        "v3rtech/v3r-core": "^0.5.0"
    },
    "repositories": [
        {
            "type": "vcs",
            "url": "https://github.com/V3RTECH-DF/V3RCore-Code.git"
        }
    ]
}
```

{: .important }
> **`require-dev`, nunca `require`.** O build de produção do plugin roda `composer install --no-dev` para gerar o autoloader final; `require` sobrevive a esse `--no-dev` e a lib acaba reinstalada **sem prefixo** dentro do próprio pacote — o zip final sai com as duas cópias, a prefixada e a original, que é exatamente o estado que colide com outro plugin da casa no mesmo WordPress. A biblioteca nunca precisa ser carregada sem prefixo em runtime; ela só existe como matéria-prima para o Strauss (item 3).

Como o repositório `V3RCore-Code` é público, `composer require` funciona sem nenhuma credencial — nem no seu ambiente, nem em CI.

## 3. Configure o Strauss

O Strauss roda como `.phar` **standalone**, nunca como dependência do Composer do seu plugin:

```bash
mkdir -p .tooling
curl -L -o .tooling/strauss.phar \
  https://github.com/BrianHenryIE/strauss/releases/download/0.19.5/strauss.phar
echo '.tooling/' >> .gitignore
```

E no `composer.json`:

```json
{
    "autoload": {
        "classmap": ["vendor-prefixed/"]
    },
    "scripts": {
        "prefix": ["php .tooling/strauss.phar compose", "composer dump-autoload"]
    },
    "extra": {
        "strauss": {
            "target_directory": "vendor-prefixed/",
            "namespace_prefix": "MeuPlugin\\Vendor\\",
            "classmap_prefix": "MeuPlugin_Vendor_",
            "constant_prefix": "MEUPLUGIN_VENDOR_",
            "packages": ["v3rtech/v3r-core"],
            "override_autoload": {
                "yahnis-elsts/plugin-update-checker": {
                    "classmap": ["Puc/"],
                    "files": ["load-v5p7.php"]
                }
            },
            "delete_vendor_packages": true
        }
    }
}
```

Troque `MeuPlugin\Vendor\`, `MeuPlugin_Vendor_` e `MEUPLUGIN_VENDOR_` pelo namespace do seu plugin — é isso que evita colisão entre dois plugins da casa com versões diferentes do `v3r-core` no mesmo site. O resto do bloco é idêntico em qualquer plugin.

{: .warning }
> **`override_autoload` para `yahnis-elsts/plugin-update-checker` é obrigatório**, mesmo você não requerendo esse pacote diretamente — ele chega como dependência transitiva do `v3r-core`, e se autoloada por um mecanismo próprio que o Strauss não enxerga sozinho. Sem este bloco, a primeira chamada ao updater é fatal error.

Crie `vendor-prefixed/` com um `.gitkeep` versionado, e ignore o resto:

```
vendor-prefixed/*
!vendor-prefixed/.gitkeep
```

{: .note }
> **Sem hooks automáticos** — `composer install` sozinho **não** gera `vendor-prefixed/`; rodar `composer run prefix` é passo explícito, à mão em desenvolvimento e automático dentro do `build-zip.sh` (item 7). É por isso que todo código do plugin que toque o `v3r-core` precisa estar protegido por `class_exists()` (item 4) — o estado "lib instalada mas ainda não prefixada" é normal logo depois de um clone.

## 4. O bootstrap

```php
<?php
declare(strict_types=1);

use MeuPlugin\Vendor\V3R\Core\Bootstrap;

$v3rCoreAutoload = __DIR__ . '/vendor-prefixed/autoload.php';
if ( file_exists( $v3rCoreAutoload ) ) {
    require_once $v3rCoreAutoload;
}

add_action( 'plugins_loaded', function () {
    if ( ! class_exists( Bootstrap::class ) ) {
        return; // vendor-prefixed/ ainda não existe — nunca fatal error, o plugin liga sem licenciamento
    }

    $licenseConfig = meuplugin_resolve_v3r_license_config(); // item 6
    if ( null === $licenseConfig ) {
        return;
    }

    $v3rCore = new Bootstrap(
        'meuplugin',                 // product_slug — precisa bater com o cadastro no V3RLicense
        __FILE__,
        $licenseConfig['api_url'],
        $licenseConfig['public_key'],
        '1.0.0',                     // versão instalada do plugin
        'meuplugin_settings_view',   // capability de leitura da licença
        'meuplugin_settings_manage'  // capability de gestão (ativar/desativar)
    );

    $v3rCore->withCapabilityDecider( function ( int $userId, string $capability ): bool {
        return MeuPlugin\Rbac::userCan( $userId, $capability );
    } );

    $v3rCore->withProductName( 'MeuPlugin' );

    $v3rCore->boot();
} );
```

{: .important }
> **`withCapabilityDecider()` é obrigatório — `boot()` lança `LogicException` sem ele.** O plugin fornece só a função de decisão (`function ( int $userId, string $capability ): bool`); **quem registra o filtro `user_has_cap` é a biblioteca**, com a guarda de saída antecipada embutida. Dentro do `$decider` você pode chamar `user_can()`/`current_user_can()` à vontade — a biblioteca só invoca `$decider` quando a capability perguntada já é uma das duas de licença, então não há recursão a evitar do seu lado.
>
> **Por que isso é rígido a esse ponto:** um filtro `user_has_cap` escrito à mão, sem a guarda de saída antecipada, fecha o ciclo `user_has_cap → user_can → user_has_cap` — infinito, e derruba **toda requisição de usuário logado** por memória esgotada, incluindo o próprio `wp-login.php`. Já aconteceu em produção. Testar só com requisição anônima (`curl` sem cookie de sessão) não revela o problema — a requisição anônima passa normalmente; é a de usuário autenticado que morre. Sempre teste logado.

As duas capabilities (`meuplugin_settings_view`/`meuplugin_settings_manage`) costumam ser **sintéticas** — pontes para um nível de permissão que já existe no RBAC do seu plugin, não capabilities nativas do WordPress. `manage_options` só é aceitável para plugin sem RBAC próprio nenhum; mesmo assim, é só um dos jeitos de errar — larga demais concede a qualquer administrador do site, estreita demais exclui quem administra o plugin sem ser administrador do WordPress.

`withProductName()` nomeia o produto no rótulo do menu e no título da tela padrão de licença — sem ele, o rótulo cai para o `productSlug`, que identifica pior num site com vários plugins da casa. Só tem efeito em quem usa a tela padrão (item 5).

## 5. A tela de licença não é opcional

{: .important }
> **Integração sem tela de licença é integração pela metade.** `boot()` sem nenhuma tela registrada não falha em nada visível — o plugin ganha o updater e as rotas REST internas, os testes passam, a ativação funciona. O que falta só aparece depois: o cliente **não tem onde informar a chave de licença**, e o `UpdateGate` recusa atualização no estado "nunca houve ativação" — **sem período de graça** (diferente do estado "ativa, mas sem contato recente", que tem 14 dias). A versão que introduz a auto-atualização é a mesma que a desliga, sem saída pela interface.

Duas opções, e as duas são válidas:

- **Tela padrão da biblioteca** — para plugin sem SPA própria. Uma linha registra a tela em PHP.
- **Aba própria, dentro do painel do plugin** — para plugin com SPA React (ou equivalente). Consome os quatro endpoints REST internos que `boot()` já expõe (`GET .../license`, `POST .../license/{activate,deactivate,refresh}`) — cada operação com a capability que você definiu no item 4.

Se o plugin tem interface própria, prefira a aba própria: a tela padrão da biblioteca não identifica de qual produto ela é a não ser pelo `withProductName()`, e num site com vários plugins da casa instalados as entradas ficam menos distinguíveis do que uma aba já integrada ao painel.

## 6. Configuração de produção: URL e chave pública

Um único par de constantes, com **os mesmos nomes em todo plugin da casa**:

```php
define( 'V3R_LICENSE_API_URL', 'https://v3rtech.com.br/wp-json/v3r-license/v1' );
define( 'V3R_LICENSE_PUBLIC_KEY', 'CHAVE_PUBLICA_ED25519_BASE64_DO_SERVIDOR' );
```

{: .warning }
> **O plugin nunca define `V3R_LICENSE_API_URL` nem `V3R_LICENSE_PUBLIC_KEY` diretamente — nem com `if ( ! defined(...) ) define(...)`.** Esses dois nomes pertencem ao `wp-config.php` do site; a existência deles ali é o único sinal de que o dono do site sobrescreveu o par (tipicamente para apontar a um servidor de licenças local, em desenvolvimento). Um `define()` condicional no topo do plugin — o padrão comum do WordPress — faz as duas constantes existirem sempre, e qualquer guard que compare "as duas vieram, ou nenhuma" deixa de distinguir wp-config de default.
>
> **O dano maior é entre plugins, não dentro de um só.** Num site com dois plugins da casa, o primeiro a carregar (ordem alfabética, que ninguém controla) define os dois nomes compartilhados com o **seu** default; o segundo encontra as duas já definidas, conclui que o site sobrescreveu o par, e passa a falar com a URL do primeiro e a conferir a chave do primeiro. Em versões diferentes — o normal — a configuração de um plugin vaza para o outro, e ninguém programou isso.
>
> **Os defaults de produção do seu plugin vão em constantes de nome próprio** (ex.: `MEUPLUGIN_LICENSE_API_URL_PADRAO`), nunca sob os nomes compartilhados. A leitura de `V3R_LICENSE_API_URL`/`V3R_LICENSE_PUBLIC_KEY` só serve para checar se o site sobrescreveu.

A decisão de qual par usar é uma função pura, separada da leitura das constantes — o que torna testável o par incoerente (só uma das duas definida) e o estado "chave de produção ainda não existe" (placeholder no build):

```php
function meuplugin_decide_v3r_license_config(
    ?string $url_do_site, ?string $chave_do_site,
    string $url_padrao, string $chave_padrao, string $placeholder
): array {
    $veio_url   = null !== $url_do_site   && '' !== $url_do_site;
    $veio_chave = null !== $chave_do_site && '' !== $chave_do_site;

    if ( $veio_url !== $veio_chave ) {
        return array( 'status' => 'incoerente' );
    }
    if ( $veio_url ) {
        return array( 'status' => 'ok', 'api_url' => $url_do_site, 'public_key' => $chave_do_site );
    }
    if ( $placeholder === $chave_padrao ) {
        return array( 'status' => 'chave_pendente' );
    }
    return array( 'status' => 'ok', 'api_url' => $url_padrao, 'public_key' => $chave_padrao );
}
```

A leitura das constantes globais fica num adaptador fino, em volta dessa função — a única parte que toca estado global, e a única que não dá para testar isoladamente.

## 7. Empacotamento (`build-zip.sh`)

Depois de gerar o `vendor/` de produção e **antes** de qualquer `dump-autoload` que o seu script rode dentro do diretório temporário do pacote:

```bash
composer install --no-interaction        # garante vendor/ fresco antes de prefixar
composer prefix --no-interaction

if [ ! -f "vendor-prefixed/v3rtech/v3r-core/src/Bootstrap.php" ]; then
  echo "ERRO: v3r-core não encontrado em vendor-prefixed/." >&2
  exit 1
fi
# guard de duas pontas — ver item 8
cp -r vendor-prefixed "$TEMP_DIR/"

( cd "$TEMP_DIR" && composer install --no-dev --no-interaction && composer dump-autoload --no-interaction )
```

{: .warning }
> **Prefixar a árvore de desenvolvimento não é prefixar o ZIP.** Confira o pacote final, não a pasta `vendor-prefixed/` do seu checkout — um passo posterior do build pode reescrever `composer.json` dentro do diretório temporário e rodar `dump-autoload` ali, quebrando a referência a `vendor-prefixed/` se a cópia não tiver acontecido antes. E `delete_vendor_packages: true` (item 3) apaga o pacote-fonte depois da primeira prefixação — um segundo `composer prefix` sem reinstalar antes "sucede" sem copiar nada, e `vendor-prefixed/` sai vazio **em silêncio**. É por isso que `composer install` roda de novo, logo antes de cada `composer prefix`, dentro do próprio script — nunca assuma que o `vendor/` de uma execução anterior ainda tem a lib.

## 8. O guard de duas pontas — confira as duas, não só uma

```php
php -r '
    require "vendor-prefixed/autoload.php";
    $prefixo = "MeuPlugin\\Vendor";
    $erros = array();
    if ( ! class_exists( $prefixo . "\\V3R\\Core\\Bootstrap" ) ) {
        $erros[] = "a classe prefixada não resolve";
    }
    if ( class_exists( "V3R\\Core\\Bootstrap" ) ) {
        $erros[] = "o namespace ORIGINAL ainda resolve";
    }
    if ( $erros ) {
        fwrite( STDERR, implode( "\n", $erros ) . "\n" );
        exit( 1 );
    }
'
```

{: .important }
> **Checar só se a classe prefixada existe não distingue "bem configurado" de "mal configurado com as duas presentes".** É esse segundo estado — namespace original **e** prefixado, os dois resolvendo — que colide com o próximo plugin da casa que embutir a mesma lib no mesmo site. O guard tem que reprovar as duas formas de errar, não só uma.

## 9. CI

**`ci.yml`**, disparado em push e pull request, com matriz de PHP:

```yaml
strategy:
  matrix:
    php: ['8.2', '8.3', '8.4']
```

Onde houver SPA própria, o build dela entra no mesmo workflow.

**`release.yml`**, disparado por tag `v*.*.*` — nunca publicação à mão:

1. Roda a suíte de testes.
2. Baixa o Strauss `.phar` e prefixa.
3. Roda o guard de duas pontas (item 8).
4. Gera o zip pelo `build-zip.sh`.
5. Confere que a versão do formulário/tag bate com o cabeçalho `Version:` do arquivo principal.
6. Publica no V3RLicense: `POST /publish` com `product_slug`, `version` e o arquivo, autenticado por `Authorization: Bearer` com o secret **`V3RLICENSE_PUBLISH_TOKEN`** — mesmo nome em todo repositório da casa.

{: .warning }
> **O produto precisa estar cadastrado no V3RLicense antes da primeira publicação** — ver **[Registrar um plugin novo](/processos/cadastrar-produto/)**, do lado de quem opera o painel. Publicar para um `product_slug` inexistente é recusado.
>
> **O token vale para um produto só.** Ao gerar o token no painel, quem opera escolhe o produto que ele autoriza publicar — um token vazado do seu repositório não publica release de outro plugin da casa. Não peça um token "genérico"; peça um escopado ao seu produto.

## Checklist antes de abrir o PR

- [ ] `Requires PHP: 8.2` no cabeçalho do arquivo principal — **não só** no `composer.json`.
- [ ] Se houver guard de versão de PHP próprio, ele está em sintaxe válida desde o PHP 7.0 (sem tipos union, `match`, promoção de propriedade, nullsafe).
- [ ] `v3rtech/v3r-core` em `require-dev` (nunca `require`), com o repositório `vcs` do `V3RCore-Code`.
- [ ] Bloco `extra.strauss` com namespace/prefixos únicos do plugin, e `override_autoload` do `plugin-update-checker` copiado tal como está.
- [ ] `vendor-prefixed/.gitkeep` versionado; o resto de `vendor-prefixed/*` no `.gitignore`.
- [ ] Todo ponto do código que toque o `v3r-core` está atrás de `class_exists()`.
- [ ] `withCapabilityDecider()` chamado antes de `boot()`.
- [ ] `withProductName()` chamado, se a tela padrão for usada.
- [ ] Existe caminho de ativação na interface — tela padrão ou aba própria consumindo os endpoints REST.
- [ ] `V3R_LICENSE_API_URL`/`V3R_LICENSE_PUBLIC_KEY` **nunca** definidas pelo plugin — só lidas; os defaults de produção vão em constantes de nome próprio.
- [ ] `build-zip.sh` reinstala antes de prefixar, copia `vendor-prefixed/` antes do `dump-autoload` do pacote, e roda o guard de duas pontas.
- [ ] `ci.yml` com matriz `['8.2', '8.3', '8.4']`; `release.yml` disparado por tag `v*.*.*`.
- [ ] Secret `V3RLICENSE_PUBLISH_TOKEN` configurado no repositório, com escopo para o produto certo.
- [ ] Produto cadastrado no painel do V3RLicense, com o slug **exatamente** igual à pasta raiz do zip.
- [ ] Testado com usuário **autenticado**, não só com requisição anônima.
