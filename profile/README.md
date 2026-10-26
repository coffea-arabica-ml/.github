# Cafélens

O Cafélens fotografa um cafeeiro e mostra, folha por folha, se ela está saudável ou tem sinais de
ferrugem, bicho-mineiro, cercosporiose ou phoma, com a severidade estimada.

É um projeto acadêmico da UNIFRAN, da disciplina Tendências em Ciência da Computação, de 2026:
**Estimativa de Severidade e Classificação de Estresses Bióticos em Folhas de *Coffea arabica* via
Aprendizado por Transferência**.

> O Cafélens é uma ferramenta de apoio e não substitui a avaliação de um engenheiro agrônomo.

## Como funciona

1. **Foto:** você fotografa a planta inteira, um galho ou uma folha, ou escolhe uma foto da galeria.
2. **Detecção das folhas:** o modelo acha cada folha da foto.
3. **Diagnóstico de cada folha:** cada folha recebe a classe (saudável, ferrugem, bicho-mineiro,
   cercosporiose ou phoma) e a severidade, e ganha um círculo sobre a foto. Tocar no círculo mostra
   o diagnóstico daquela folha.

## Usar o Cafélens

- **Site:** <https://coffea-web.vercel.app>
- **App Android (`v1.0.0`):**
  - [`cafelens-apresentacao.apk`](https://github.com/coffea-arabica-ml/coffea-mobile/releases/latest/download/cafelens-apresentacao.apk):
    envia a foto ao servidor do projeto, que roda o modelo real. Depende de internet e de o
    servidor estar no ar.
  - [`cafelens-demonstracao.apk`](https://github.com/coffea-arabica-ml/coffea-mobile/releases/latest/download/cafelens-demonstracao.apk):
    modo demonstração, com resultados simulados, sem precisar de internet.
  - [Página da release](https://github.com/coffea-arabica-ml/coffea-mobile/releases/latest)
- **iPhone:** não há versão para iPhone. Use o site.

## Repositórios

| repositório | o que tem |
|---|---|
| [`coffea-ml`](https://github.com/coffea-arabica-ml/coffea-ml) | dados, treino e avaliação do modelo: o detector de folhas e o classificador de estresse e severidade |
| [`coffea-backend`](https://github.com/coffea-arabica-ml/coffea-backend) | API (FastAPI) que roda o modelo e guarda o histórico; é o servidor do site e do APK de apresentação |
| [`coffea-web`](https://github.com/coffea-arabica-ml/coffea-web) | o site (React, Vite e TypeScript) |
| [`coffea-mobile`](https://github.com/coffea-arabica-ml/coffea-mobile) | o app Android (Expo / React Native) e a release `v1.0.0`, com os APKs |

## Resultados

No teste fechado do BRACOL, aberto uma única vez, com o modelo congelado:

- **Classificador sozinho:** acurácia de 90,5% (intervalo de confiança de 86,3% a 93,5%).
- **Cadeia final** (detector, classificador e regras de decisão), sem o corte de confiança:
  acurácia de 88,1% (83,5% a 91,5%).

O BRACOL tem folhas isoladas, sobre fundo claro. Os outros resultados (detecção no BRACOT e folhas
de campo) e as limitações estão no README do
[`coffea-ml`](https://github.com/coffea-arabica-ml/coffea-ml), seção "Testes fechados".

## Dados e licenças

- **Código:** AGPL-3.0, nos 4 repositórios (arquivo `LICENSE` de cada um).
- **Modelos entregues:** o classificador foi treinado com o BRACOL, e o detector de folhas, com o
  BRACOT, os dois sob CC BY 4.0. O detector parte do peso pré-treinado YOLO11s-seg do ultralytics,
  que é AGPL-3.0.
- **Só nos experimentos:** o JMuBEN e o JMuBEN2 (CC BY 4.0) entraram só em variantes de treino
  comparadas no `coffea-ml`; nenhuma delas virou o modelo entregue.
- **Citações dos dados:** a CC BY 4.0 exige citar os autores. As citações completas estão em
  [`coffea-ml/data/README.md`](https://github.com/coffea-arabica-ml/coffea-ml/blob/main/data/README.md).

## Participar

- [Guia de contribuição](https://github.com/coffea-arabica-ml/.github/blob/main/CONTRIBUTING.md)
- [Código de conduta](https://github.com/coffea-arabica-ml/.github/blob/main/CODE_OF_CONDUCT.md)
- [Política de segurança](https://github.com/coffea-arabica-ml/.github/blob/main/SECURITY.md):
  vulnerabilidades vão pelo relato privado do GitHub, nunca por issue pública.
- **Como citar:** o `CITATION.cff` de cada repositório (no GitHub, o botão "Cite this repository",
  na página do repositório).

## Summary in English

Cafélens is an academic project from UNIFRAN (Brazil, 2026). From a photo of a coffee plant
(*Coffea arabica*), it detects each leaf and classifies it as healthy or affected by rust, leaf
miner, cercospora leaf spot or phoma, with an estimated severity. It runs as a website
(https://coffea-web.vercel.app) and as an Android app (see the `coffea-mobile` releases). The code is
licensed under AGPL-3.0; the delivered models were trained on the BRACOL and BRACOT datasets (CC BY
4.0). The documentation is in Portuguese.
