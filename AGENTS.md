# AGENTS.md

Instruções para qualquer assistente de código que usarmos neste projeto (Claude Code, Codex, Copilot, Cursor etc.).
Leia este arquivo inteiro antes de começar e siga as regras abaixo em toda tarefa.

## Contexto

Este repositório é o seminário do nosso grupo de 4 alunos para a disciplina Tópicos em Redes Complexas (UFSCar).
Vamos apresentar e replicar o artigo:

> Giudici, Hadji-Misheva & Spelta (2019). *Network Based Scoring Models to Improve Credit Risk Management in Peer to
> Peer Lending Platforms.* Frontiers in Artificial Intelligence, 2:3. PDF em `docs/artigo/giudici2019.pdf`.

O prazo final é 02/12/2026 (slides em PDF). O cronograma e a divisão de tarefas estão em `CRONOGRAMA.md` e `README.md`.

## Como escrever

Tudo o que for para o repositório (README, markdown, comentários de código, células de texto dos notebooks,
mensagens de commit) deve parecer escrito pelo grupo.

- Português do Brasil, na primeira pessoa do plural: "calculamos", "vamos testar", "nós usamos".
- Não mencionar ferramentas de IA, assistentes ou modelos de linguagem em nenhum arquivo versionado.
- Nada de travessões longos (—), setas unicode (→) ou emojis no texto. Use vírgula, dois-pontos ou parênteses.
- Frases diretas e curtas. Sem introduções do tipo "Neste notebook, iremos explorar..." nem resumos repetindo o que
  acabou de ser dito.
- Comentários de código só onde explicam algo que não é óbvio (uma escolha do artigo, uma correção nossa).
  Não comente linha por linha.

## Commits

- Mensagem curta em português, no presente e na 3ª pessoa: `Adiciona cálculo da MST`, `Corrige pesos do Louvain`.
- **Nunca** adicione `Co-Authored-By`, assinaturas ou rodapés gerados automaticamente.
- Um commit por mudança lógica. Não misture refatoração com resultado novo.
- Nunca faça `push`, `push --force`, `rebase` ou altere o histórico sem pedir antes.

## Ambiente

- Python 3.12, com ambiente virtual em `.venv/` na raiz do repositório.
- Bibliotecas que já usamos nas aulas: `numpy`, `pandas`, `scipy`, `networkx`, `igraph`, `scikit-learn`,
  `statsmodels`, `matplotlib`, `jupyterlab`. Prefira essas antes de adicionar outra dependência.
- Toda dependência nova vai para `requirements.txt`.
- Se o código do Supplementary Material estiver em R, mantemos a referência em R e reimplementamos em Python.

## Estrutura e dados

| Pasta | Conteúdo | Regras |
|---|---|---|
| `data/` | Bases de dados | Fora do Git. **Nunca** modificar, sobrescrever ou apagar arquivos aqui. Ler e salvar derivados em `data/processed/` |
| `src/` | Scripts e notebooks | Notebooks numerados pela etapa: `01_dados.ipynb`, `02_mst.ipynb`, `03_modelos.ipynb`... |
| `results/` | Figuras e tabelas geradas pelo código | Tudo aqui deve poder ser recriado rodando `src/` |
| `slides/` | Apresentação e PDF final | |
| `docs/` | Artigo e anotações das reuniões | |

- Nunca versionar bases de dados nem arquivos acima de 50 MB.
- Caminhos sempre relativos à raiz do repositório, nunca absolutos (`C:\Users\...`).

## Método do artigo (o que precisamos replicar)

1. **Distância:** euclidiana padronizada entre os vetores de índices financeiros,
   d(i,j) = sqrt( soma_t (x_it - x_jt)^2 / s_t^2 ), com s_t o desvio-padrão da variável t.
2. **Rede:** Minimal Spanning Tree sobre a matriz de distâncias (Kruskal, equivalente ao single linkage).
3. **Medidas por nó:** grau e força na MST; comunidade pelo Louvain.
4. **Modelos:** Logit, LDA, CART e SVM, com e sem as variáveis de rede.
5. **Avaliação:** 10 divisões aleatórias treino/teste; média de AUC, KS, Gini (= 2·AUC − 1) e acurácia.
6. **Alvo da replicação (Tabela 2):** AUC da Logit 79,63 sem rede e 80,79 com rede; LDA 77,76 e 79,16;
   SVM 76,81 e 77,65; CART 67,97 nos dois casos.

### Erros conhecidos no artigo

Não copie as fórmulas do PDF sem conferir:

- Eq. (2): falta o sinal negativo. O correto é p = 1 / (1 + exp(-(α + Σ β x))).
- Eq. (7): falta a raiz quadrada, e a matriz deve ter as variâncias, não os desvios-padrão.
- Eq. (8) e (9): grau e força se referem à adjacência da MST, não à matriz completa de distâncias.
- Eq. (10): o correto é s_i·s_j e δ(c_i, c_j).
- Tabela 2: algumas colunas de KS e Gini estão trocadas (SVM e CART). Confira sempre com Gini = 2·AUC − 1.

### Nossas correções (contribuição do grupo)

Mantenha sempre a versão "como no artigo" e a versão corrigida lado a lado, para podermos comparar:

- Teste de DeLong e intervalos de confiança entre as 10 divisões.
- Rede construída só com o conjunto de treino. O artigo parece montar a rede com todas as empresas antes de separar o
  teste e não explica como pontuar uma empresa nova. A rede usa só os índices financeiros, não o default, então não é
  vazamento do rótulo; o problema é que o cenário não corresponde a uma plataforma real.
- Louvain com pesos de similaridade (1/d ou exp(-d)) em vez de distância.

## Reprodutibilidade

- Fixe a semente em todo código aleatório: `SEED = 42`.
- Notebooks devem rodar do início ao fim sem erro (Restart & Run All) antes do commit.
- Nunca invente ou arredonde resultados para "bater" com o artigo. Se não bater, registre a diferença e investigue.

## Registro de uso

O enunciado da disciplina (seção 1.6) exige um slide final com as ferramentas usadas e para quê. Ao terminar cada
tarefa, acrescente uma linha em `registro.local.md` na raiz (arquivo local, fora do Git) no formato:

```
AAAA-MM-DD | ferramenta | tarefa | arquivos tocados
```

## Antes de entregar qualquer tarefa

- [ ] O código roda do zero.
- [ ] Nenhum arquivo em `data/` foi alterado.
- [ ] Texto na primeira pessoa do plural, sem menções a ferramentas.
- [ ] Commit sem `Co-Authored-By`.
- [ ] Explique ao integrante o que foi feito: todos precisam conseguir defender qualquer parte na arguição.
