# Material de apoio da reunião inicial (09/11/2026)

## 1. Do que o artigo trata, explicado do zero

### O problema

Imagine um site onde pessoas comuns emprestam dinheiro diretamente para pequenas empresas, sem banco no meio. É isso
que se chama **P2P lending** (*peer-to-peer*, "de par para par").

A pergunta central de qualquer empréstimo é: **essa empresa vai me pagar ou vai dar calote?** Calote, no jargão, é
*default*.

Para responder, as plataformas usam um **modelo de credit scoring**: uma fórmula estatística que recebe dados da empresa
e devolve uma nota, ou uma probabilidade de calote. Por exemplo: "esta empresa tem 15% de chance de não pagar".

### Os dados que o modelo usa

Os dados de entrada são **índices financeiros** tirados do balanço de cada empresa, como:

- quanto ela deve em relação ao que tem (endividamento);
- se ela tem dinheiro para pagar as contas de curto prazo (liquidez);
- quanto lucra em relação ao que fatura (margem).

O modelo tradicional olha **cada empresa isoladamente**: pega os índices dela e calcula a nota.

### A ideia nova do artigo

Os autores perguntam: **e se olharmos as empresas em relação às outras?**

A intuição é algo como *"diga-me com quem te pareces e te direi quem és"*. Se uma empresa tem um balanço muito parecido
com o de outras que deram calote, isso é um sinal de alerta, mesmo que os números dela, olhados sozinhos, não pareçam
tão ruins.

Para capturar isso, eles constroem uma **rede**:

- **cada nó é uma empresa** (4.514 PMEs italianas);
- **duas empresas ficam ligadas se seus balanços forem parecidos.**

### Como a rede é construída (em 3 passos)

**Passo 1: medir a "distância" entre empresas.** Para cada par de empresas, calcula-se o quão diferentes são os
balanços. Distância pequena significa empresas parecidas. Antes, cada índice é padronizado para que um índice com
números grandes (como o faturamento) não domine os outros.

**Passo 2: filtrar a rede.** Ligando todo mundo com todo mundo, ficariam cerca de 10 milhões de conexões, o que é
inútil. Por isso os autores usam a **Árvore Geradora Mínima (MST)**: mantêm só as ligações mais fortes, de modo que cada
empresa fique conectada às mais parecidas com ela, sem formar ciclos. Sobram só 4.513 ligações, que formam a "espinha
dorsal" da similaridade.

**Passo 3: extrair informação da posição de cada empresa na rede.**

- **Grau:** quantas empresas estão ligadas a ela. Uma empresa com grau 1 é uma **folha**, fica na ponta da árvore e é
  "diferente" da maioria.
- **Força:** a soma das distâncias até os vizinhos. Força alta indica uma empresa isolada, ligada por conexões fracas.
- **Comunidade:** em qual "grupo" de empresas parecidas ela está, encontrado pelo algoritmo de Louvain.

### O resultado principal

Quando pintam a árvore, com as empresas que deram calote em vermelho, aparece um padrão: **as caloteiras ficam nas
pontas da árvore (folhas) e aparecem agrupadas.**

Então eles pegam o modelo de scoring tradicional e **acrescentam grau, força e comunidade como variáveis extras**.
Comparam os dois:

| | Sem rede | Com rede |
|---|---|---|
| Regressão logística (AUC) | 79,6 | **80,8** |

A previsão **melhora um pouco**, cerca de 1 ponto. Para entender o número: a **AUC** mede o quão bem o modelo separa
quem paga de quem não paga. 50 equivale a um chute e 100 a um acerto perfeito.

### Em uma frase

> *Empresas com balanços parecidos tendem a ter destinos parecidos. Representar isso como rede e usar a posição de
> cada empresa nela como informação extra melhora a previsão de calote.*

### Por que esse artigo tem espaço para a nossa contribuição

O artigo é **curto e tem falhas**. Isso é bom para o trabalho, porque abre espaço para contribuirmos:

- a melhora de 1 ponto pode ser **sorte**, já que eles não fazem teste estatístico;
- a rede é montada **com todas as empresas, inclusive as que deveriam ficar escondidas para o teste** (isso se chama
  vazamento de dados);
- há **erros nas fórmulas**.

A nossa contribuição é justamente refazer o estudo e corrigir esses pontos.

## 2. Como isso vira 4 papéis

O artigo tem uma estrutura em forma de "linha de montagem". Cada papel é uma etapa dessa linha:

```
Dados ──> Distância + MST ──> Medidas de rede ──> Modelos de previsão ──> Crítica e correções
  └──────── A ─────────┘      └────── B ─────┘    └──────── C ───────┘    └─────── D ───────┘
```

| Papel | Pergunta que responde | Seções do artigo | Fala na apresentação |
|---|---|---|---|
| **A: Dados e rede** | Como transformamos empresas numa rede? | Introdução, Sec. 2 (dados), 2.3 e 2.4 | Contexto P2P e dados |
| **B: Medidas de rede** | O que a posição na rede diz sobre a empresa? | Sec. 2.5 e Figura 1 | Conceitos preliminares (MST, Louvain, modularidade) |
| **C: Modelos** | Com a rede, a previsão melhora? | Sec. 2.1, 2.2, 3 e Tabela 2 | Método e resultados |
| **D: Crítica** | Dá para confiar nisso? O que está errado ou falta? | Artigo inteiro, com olhar crítico | Análise crítica e contribuição |

**Para escolher os papéis:** quem gosta mais de **programar** fica bem com A ou C. Quem prefere **teoria e grafos**
fica bem com B. Quem tem **olhar mais crítico** e gosta de estatística fica bem com D.

## 3. Como fazer a releitura

O artigo tem só 7 páginas. Vamos fazer **duas leituras** com objetivos diferentes.

**Leitura 1, todos nós até sexta (13/11): leitura panorâmica**

- Ler do começo ao fim sem travar nas fórmulas.
- Objetivo: conseguir explicar a ideia em uma frase, como na seção 1.
- Olhar com atenção a **Figura 1** (a árvore colorida) e a **Tabela 2** (os resultados).

**Leitura 2, cada um a sua parte até domingo (15/11): leitura profunda**

- Cada um lê **em detalhe** as seções do próprio papel, conferindo cada fórmula.
- Anota as dúvidas e o que não entendeu.
- Na reunião de domingo, **cada um explica a sua parte para os outros três em 5 minutos**. Esse é o melhor treino
  para a arguição.
