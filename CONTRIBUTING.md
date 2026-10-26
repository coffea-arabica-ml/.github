# Como contribuir com o Cafélens

Este guia vale para os repositórios da organização
[coffea-arabica-ml](https://github.com/coffea-arabica-ml) que não tiverem um guia próprio. Quem
participa segue o
[código de conduta](https://github.com/coffea-arabica-ml/.github/blob/main/CODE_OF_CONDUCT.md).

## Abrir uma issue

1. Procure nas issues do repositório, abertas e fechadas, se o assunto já apareceu.
2. Abra a issue no repositório da parte afetada:
   - site: `coffea-web`;
   - app Android: `coffea-mobile`;
   - API e servidor: `coffea-backend`;
   - modelo e dados: `coffea-ml`.
3. Escolha o modelo **Relato de problema** ou **Sugestão de melhoria** e preencha os campos.
4. Não ponha na issue senha, chave, token, conteúdo de `.env` nem dados pessoais.

Vulnerabilidade não vira issue: siga a
[política de segurança](https://github.com/coffea-arabica-ml/.github/blob/main/SECURITY.md).

## Fluxo de trabalho

- **Time do projeto:** trabalha direto na `main`, sem branch nem pull request (decisão do gestor do
  projeto, 16/10/2026).
- **Quem é de fora:** faça um fork, trabalhe numa branch do fork e abra um pull request para a
  `main` do repositório. O gestor do projeto revisa e decide se entra.
- **Pull request:** um assunto por vez. O modelo de pull request pede o que muda, como foi testado
  e um checklist.

## Rodar os testes

Os comandos vêm dos READMEs de cada repositório, que têm os detalhes.

### `coffea-ml`

No PowerShell, na raiz do repositório (`data/README.md`, "Reproduzir do zero" e "Comandos"):

```
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
python -m pytest
```

- Os testes do manifest versionado não precisam das imagens.
- Sem o ultralytics, os testes do detector que dependem dele são pulados. Para rodá-los, instale-o
  depois do `requirements.txt`, como manda o README (seção "Ambiente"):
  `pip install --no-deps ultralytics==8.4.175`.

### `coffea-backend`

README, "Rodando localmente" e "Testes":

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
pip install -r requirements.txt
pip install --no-deps ultralytics==8.4.175
pip install -r requirements-dev.txt
python -m pytest                        # tudo
python -m pytest -m "not modelo_real"   # só a suíte que roda sem os pesos
```

A suíte `modelo_real` usa os pesos reais e o `coffea-ml` ao lado, e é pulada quando os pesos não
estão na máquina.

### `coffea-web`

README, "Rodando localmente" e "Scripts":

```bash
npm install
npm test            # Vitest
npm run typecheck
npm run lint        # Oxlint
```

### `coffea-mobile`

README, "Scripts":

```bash
npm install
npm run typecheck
npm test            # jest-expo
```

Para conferir se o bundle compila sem celular: `npx expo export --platform android`.

## Commits

- Em português, no imperativo: "Adiciona ...", "Corrige ...", "Atualiza ...".
- No `coffea-ml`, sem acento: "Atualiza a secao de validacao", e não "Atualiza a seção de
  validação".

## Regras da versão acadêmica (`v1.0.0`)

A `v1.0.0` é a versão acadêmica do Cafélens. Duas regras valem para qualquer contribuição:

- **O modelo está congelado.** Nenhum parâmetro nem limiar muda: nem os padrões de
  `inferencia.Configuracao`, no `coffea-ml`, nem os pesos publicados na Release `pesos-v1`. Na
  versão acadêmica, pull request que mude o modelo não entra.
- **Os conjuntos de teste fechados nunca mais podem ser usados**, para nada: treino, ajuste,
  avaliação, testes automatizados ou medições. São eles:
  - o teste do BRACOL (o split `teste` de `data/manifests/bracol.csv`);
  - a pasta `test/` do BRACOT;
  - as folhas de campo do teste (`data/manifests/campo_rotulado_teste.csv`).

  Por isso, não rode `model/teste_final.py` nem as opções `--avaliar-teste` do `coffea-ml`.

Correções, testes, documentação e melhorias que respeitem as duas regras são bem-vindas.

## O que nunca vai para o git

- segredos: senhas, chaves, tokens e o conteúdo de `.env` (o modelo é o `.env.example` do
  repositório, quando houver);
- pesos de modelo (`.pt`): ficam fora do git, com nome, tamanho e SHA-256 em
  `coffea-ml/model/pesos/MANIFESTO.md`;
- o banco do histórico do `coffea-backend`, `coffea.db`;
- as imagens dos conjuntos de dados (`coffea-ml/data/README.md`).

## Licença das contribuições

O código dos repositórios é distribuído sob a AGPL-3.0 (arquivo `LICENSE` de cada um). Ao enviar
uma contribuição, você concorda que ela entra sob essa mesma licença.

## Dados de terceiros (CC BY 4.0)

Os modelos e os experimentos usam conjuntos de dados públicos sob a licença CC BY 4.0, que exige
citar os autores. Quem usar os dados, os modelos ou os resultados precisa citar:

- **BRACOL** (classificador entregue): Krohling, Esgario e Ventura (2019), Mendeley Data, versão 1,
  DOI [10.17632/yy2k5y8mxg.1](https://doi.org/10.17632/yy2k5y8mxg.1).
- **BRACOT** (detector de folhas entregue): Krohling, Tozzi de Souza e Tassis (2021), Mendeley
  Data, versão 1, DOI [10.17632/pmkbyjpf6k.1](https://doi.org/10.17632/pmkbyjpf6k.1).
- **JMuBEN** (só experimentos): Jepkoech, Kenduiywo, Mugo e Chebet (2021), Mendeley Data, versão
  1, DOI [10.17632/t2r6rszp5c.1](https://doi.org/10.17632/t2r6rszp5c.1).
- **JMuBEN2** (só experimentos): Jepkoech, Mugo, Kenduiywo e Chebet (2021), Mendeley Data, versão
  1, DOI [10.17632/tgv3zb82nd.1](https://doi.org/10.17632/tgv3zb82nd.1).
- **Artigo de referência do JMuBEN e do JMuBEN2:** Jepkoech, Mugo, Kenduiywo e Too, *Data in
  Brief*, v. 36, art. 107142, 2021.

A procedência e a licença de cada cópia estão em
[`coffea-ml/data/README.md`](https://github.com/coffea-arabica-ml/coffea-ml/blob/main/data/README.md).
