# Seminário de Redes Complexas: Network-Based Credit Scoring

Este é o repositório do nosso seminário para a disciplina **Tópicos em Redes Complexas** (UFSCar, Prof.ª Andressa Cerqueira).

## Artigo

Giudici, P., Hadji-Misheva, B. & Spelta, A. (2019).
*Network Based Scoring Models to Improve Credit Risk Management in Peer to Peer Lending Platforms.*
Frontiers in Artificial Intelligence, 2:3. DOI: [10.3389/frai.2019.00003](https://doi.org/10.3389/frai.2019.00003)

- PDF: [docs/artigo/giudici2019.pdf](docs/artigo/giudici2019.pdf) (o artigo é de acesso aberto, licença CC BY)
- Dados e código dos autores: [Supplementary Material](https://www.frontiersin.org/articles/10.3389/frai.2019.00003/full#supplementary-material)

Os autores constroem uma rede de similaridade entre 4.514 PMEs italianas a partir de índices de balanço. A distância
entre duas empresas é a euclidiana padronizada, e a rede é filtrada por uma Minimal Spanning Tree. De cada empresa
eles extraem grau, força e comunidade (Louvain) e usam essas medidas como variáveis extras em modelos de credit
scoring (Logit, LDA, CART e SVM).

Nós vamos replicar esses resultados, corrigir alguns pontos do método e, se der tempo, aplicá-lo a outra base.

## Grupo

| Integrante | Código | Apresentação |
|---|---|---|
| A: _nome_ | Dados, distância e MST | Contexto P2P e dados |
| B: _nome_ | Medidas de rede e Louvain | Conceitos preliminares |
| C: _nome_ | Modelos, métricas e replicação | Método e resultados |
| D: _nome_ | DeLong, correções e extensões | Análise crítica e contribuição |

## Datas

| Etapa | Data |
|---|---|
| Envio do artigo para aprovação | 30/10/2026 |
| **Entrega dos slides (PDF)** | **02/12/2026, até 18h** |
| Apresentações (25 min, ordem sorteada) | 03 e 04/12/2026 |

O cronograma completo está em [CRONOGRAMA.md](CRONOGRAMA.md).

## Etapas

```
1. Dados ──> 2. Replicação ──> 3. Correções ──> 4. Extensões ──> 5. Slides
```

1. **Dados:** baixar e conferir a base do Supplementary Material.
2. **Replicação:** MST, Louvain e os quatro modelos, tentando chegar perto da Tabela 2 do artigo.
3. **Correções:** teste de DeLong, rede construída só com o treino e Louvain com similaridade no lugar da distância.
4. **Extensões (opcional):** base da Bondora e outras centralidades.
5. **Slides.**

## Organização das pastas

```
├── README.md
├── CRONOGRAMA.md        cronograma e checklist de cada semana
├── requirements.txt     bibliotecas Python
├── data/                bases de dados (fora do Git, ver data/README.md)
├── src/                 scripts e notebooks
├── results/             figuras e tabelas geradas pelo código
├── slides/              apresentação e PDF final
└── docs/
    ├── artigo/          PDF do artigo
    └── reunioes/        anotações das nossas reuniões
```

## Nossas combinações

1. Sempre damos `git pull` antes de começar a mexer em qualquer coisa.
2. Fazemos commits pequenos, com uma mensagem que diga o que mudou (ex.: `Adiciona cálculo da MST`).
3. Não subimos bases de dados nem arquivos grandes. O `.gitignore` já deixa a pasta `data/` de fora.
