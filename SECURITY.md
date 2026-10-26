# Política de segurança

Vale para os repositórios da organização
[coffea-arabica-ml](https://github.com/coffea-arabica-ml) que não tiverem uma política própria,
para o site e para o servidor do projeto.

## Versões com suporte

| versão | suporte |
|---|---|
| `v1.0.0` (versão acadêmica) | sim |
| anteriores | não |

A `v1.0.0` está publicada como release no
[`coffea-mobile`](https://github.com/coffea-arabica-ml/coffea-mobile/releases/latest).

## Como relatar uma vulnerabilidade

Use o relato privado de vulnerabilidade do próprio GitHub, no repositório afetado:

1. Abra o repositório no GitHub:
   - site: `coffea-web`;
   - app Android: `coffea-mobile`;
   - API e servidor: `coffea-backend`;
   - modelo e dados: `coffea-ml`.
2. Clique na aba **Security** (o GitHub pode mostrá-la como **Security and quality**).
3. Clique em **Report a vulnerability**, preencha o formulário e envie.

O relato é privado: só os mantenedores do repositório e quem relatou o veem.

**Não abra issue pública** sobre uma vulnerabilidade, nem a comente em issue, pull request ou
outro lugar público.

## O que não fazer

Não faça teste de carga, varredura nem ataque contra o servidor do projeto ou o site. Para testar,
rode o projeto na sua máquina, como explicam os READMEs. O site e o app também têm um modo
simulado, que não usa o servidor.

## Prazo de resposta

O Cafélens é um projeto acadêmico: a resposta não tem prazo garantido.
