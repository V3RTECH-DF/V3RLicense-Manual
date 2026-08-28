---
title: Preparar um plugin para o V3RLicense
nav_order: 8
has_children: true
---

# Preparar um plugin para o V3RLicense

Esta seção é para **desenvolvedor** — quem vai fazer um plugin WordPress da casa falar com o V3RLicense: receber licenciamento e auto-atualização. Não é para quem opera o painel (essa trilha é o resto deste manual, a partir de **[Como faço…](/processos/)**).

O que dá o licenciamento e a auto-atualização a um plugin é a biblioteca **`v3rtech/v3r-core`** — um pacote Composer, mantido no repositório público [`V3RTECH-DF/V3RCore-Code`](https://github.com/V3RTECH-DF/V3RCore-Code), na tag **`v0.5.0`**. Ela fica embutida (prefixada) dentro do zip de cada plugin distribuído — o plugin cliente não faz nenhuma chamada de rede além das que o `v3r-core` já faz para o V3RLicense.

{: .note }
> **Se você só quer entender a política de licenciamento** — o que uma licença dá direito, o que acontece quando vence — isso não é aqui; é em **[Como funciona a licença](/como-funciona/)**. Esta seção é sobre código: como fazer o plugin falar com o servidor.

## Duas trilhas

- **[Plugin novo, do zero](/integrar-plugin/plugin-novo/)** — você está começando um plugin da casa agora e quer nascer já integrado, sem retrabalho depois.
- **[Integrar um plugin existente](/integrar-plugin/plugin-existente/)** — o plugin já roda em produção, sem licenciamento, e você vai adicioná-lo agora.

As duas convergem no mesmo lugar: um `Bootstrap` instanciado, uma função de decisão de capability, uma tela onde o cliente informa a chave, e uma pipeline que publica por tag. A diferença é só o ponto de partida.

## O que você precisa ter em mãos antes de começar

- **PHP 8.2 no ambiente de build** (dev e CI) — é o piso da casa, ver checklist de cada trilha para onde ele precisa ser declarado.
- **Composer 2.x**.
- Acesso ao repositório público `V3RTECH-DF/V3RCore-Code` (não exige credencial — é público desde 27/08/2026).
- O **slug do produto** já decidido — precisa bater, depois, com a pasta raiz do zip e com o cadastro no painel do V3RLicense (veja **[Registrar um plugin novo](/processos/cadastrar-produto/)**, do lado de quem opera).

## Glossário rápido

- **Strauss** — ferramenta que reescreve o namespace PHP de uma dependência, para duas cópias diferentes da mesma lib (em dois plugins distintos, no mesmo WordPress) não colidirem em runtime (`Cannot redeclare class`). Roda como binário `.phar` avulso, não como dependência do Composer do seu plugin.
- **Prefixar** — o que o Strauss faz: trocar `V3R\Core\Bootstrap` por algo como `MeuPlugin\Vendor\V3R\Core\Bootstrap`, único por plugin.
- **`vendor-prefixed/`** — a pasta com o resultado da prefixação; é o que vai para produção. `vendor/v3rtech/v3r-core`, a cópia crua, não deveria sobreviver ao empacotamento.
- **`Bootstrap`** — a classe de entrada do `v3r-core`; um plugin instancia uma, configura e chama `boot()`.
- **`UpdateGate`** — a peça do `v3r-core` que decide se o plugin recebe aviso de atualização, a partir do estado da licença.
