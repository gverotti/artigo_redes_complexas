# Seminário de Redes Complexas — Network-Based Credit Scoring

Trabalho da disciplina **Tópicos em Redes Complexas** (UFSCar, Prof.ª Andressa Cerqueira).

## Artigo

Giudici, P., Hadji-Misheva, B. & Spelta, A. (2019).
*Network Based Scoring Models to Improve Credit Risk Management in Peer to Peer Lending Platforms.*
Frontiers in Artificial Intelligence, 2:3. DOI: [10.3389/frai.2019.00003](https://doi.org/10.3389/frai.2019.00003)

- PDF: [docs/artigo/giudici2019.pdf](docs/artigo/giudici2019.pdf) (acesso aberto, licença CC BY)
- Dados e código originais: [Supplementary Material](https://www.frontiersin.org/articles/10.3389/frai.2019.00003/full#supplementary-material)

**Ideia do artigo:** construir uma rede de similaridade entre 4.514 PMEs italianas a partir de índices de balanço
(distância euclidiana padronizada → Minimal Spanning Tree), extrair grau, força e comunidades (Louvain) de cada nó
e usá-los como variáveis extras em modelos de credit scoring (Logit, LDA, CART, SVM).

## Grupo

| Integrante | Papel no código | Parte na apresentação |
|---|---|---|
| A — _nome_ | Dados + distância + MST | Contexto P2P e dados |
| B — _nome_ | Medidas de rede + Louvain | Conceitos preliminares |
| C — _nome_ | Modelos + métricas + replicação | Método formal + resultados |
| D — _nome_ | DeLong + correções + extensões | Análise crítica + contribuição + slide de IA |

## Datas

| Etapa | Data |
|---|---|
| Envio do artigo para aprovação | 30/10/2026 |
| **Entrega dos slides (PDF)** | **02/12/2026, até 18h** |
| Apresentações (25 min, ordem sorteada) | 03 e 04/12/2026 |

Cronograma detalhado: [CRONOGRAMA.md](CRONOGRAMA.md)

## Pipeline

```
1. Dados ──> 2. Replicação ──> 3. Correções ──> 4. Extensões ──> 5. Slides
 (suppl.      (MST + Louvain    (DeLong, rede     (Bondora,
  material)    + 4 modelos,      só no treino,     outras
               bater Tab. 2)     similaridade)     centralidades)
```

## Estrutura do repositório

```
├── README.md            este arquivo
├── CRONOGRAMA.md        cronograma e checklist semanal
├── data/                dados (NÃO versionados — ver data/README.md)
├── src/                 código (scripts/notebooks)
├── results/             figuras e tabelas geradas pelo código
├── slides/              fonte dos slides e PDF final
└── docs/
    ├── artigo/          PDF do artigo
    └── reunioes/        atas das reuniões do grupo
```

## Como contribuir

1. `git pull` antes de começar a trabalhar.
2. Commits pequenos, com mensagem dizendo o que mudou (`"Adiciona cálculo da MST"`).
3. Não versionar dados brutos nem arquivos acima de ~50 MB (o `.gitignore` já cuida dos dados).
4. Registrar no slide de IA qualquer uso de ferramentas de IA (exigência do enunciado).
