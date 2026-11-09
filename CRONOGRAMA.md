# Cronograma

**Prazo final: quarta, 02/12/2026, até 18h** (slides em PDF). Apresentações em 03 e 04/12 — ordem sorteada,
então todos precisam estar prontos desde o primeiro dia.

Marque `[x]` conforme as tarefas forem concluídas (o GitHub mostra as caixas como checklist).

---

## Semana 1 — Base (09–15/11)

- [ ] Reunião de kickoff: dividir papéis e preencher os nomes no [README](README.md#grupo)
- [ ] Todos leem o artigo inteiro
- [ ] Confirmar com a professora que o artigo foi aprovado
- [ ] Baixar o Supplementary Material e documentar o conteúdo em `data/README.md`
- [ ] Definir linguagem (R ou Python), de preferência a mesma do código original
- [ ] Definir ferramenta e template dos slides
- [ ] Todos com acesso ao repositório (clone + primeiro commit de teste)

## Semana 2 — Replicação (16–22/11)

> ⚠️ 20/11 (sexta) é feriado.

- [ ] **A:** carregar os dados, matriz de distância euclidiana padronizada, MST (Kruskal)
- [ ] **B:** grau, força e comunidades (Louvain) de cada nó; figura da MST colorida por default (Figura 1)
- [ ] **C:** Logit, LDA, CART e SVM com 10 divisões aleatórias treino/teste; AUC, KS, Gini e acurácia
- [ ] **Meta:** chegar perto da Tabela 2 (AUC da Logit ≈ 79,6 → 80,8)
- [ ] **D:** rascunho dos slides de conceitos preliminares (MST, modularidade, ROC/AUC)
- [ ] Reunião de fim de semana: cada um explica sua parte para os outros três

## Semana 3 — Contribuição + slides (23–29/11)

- [ ] Teste de DeLong e intervalos de confiança entre as 10 divisões
- [ ] Rede construída **só com o treino** (versão sem vazamento de dados)
- [ ] Louvain com similaridade (1/d ou exp(−d)) em vez de distância
- [ ] *Opcional:* aplicar o método na Bondora
- [ ] *Opcional:* trocar a MST por kNN ou rede por limiar; outras centralidades (betweenness, PageRank)
- [ ] **27/11 (sex): primeira versão completa dos slides**
- [ ] **28 ou 29/11: primeiro ensaio cronometrado (25 min)**

## Semana 4 — Fechamento (30/11–02/12)

- [ ] 30/11 (seg): ajustes a partir do ensaio
- [ ] 01/12 (ter): segundo ensaio + gerar PDF + revisar slide de uso de IA
- [ ] **02/12 (qua): enviar o PDF** — meta até 12h, limite 18h
- [ ] 03–04/12: apresentação

---

## Conteúdo obrigatório dos slides (enunciado)

- [ ] Contextualização (problema, motivação, literatura)
- [ ] Conceitos preliminares (tudo que não foi visto em aula)
- [ ] Modelo/método formal (notação, hipóteses, relação com a disciplina)
- [ ] Resultados principais
- [ ] Análise crítica (limitações, hipóteses restritivas, extensões)
- [ ] Contribuição própria do grupo
- [ ] Slide final de uso de IA (ferramentas e finalidades)

## Divisão da apresentação (25 min)

| Integrante | Bloco | Tempo |
|---|---|---|
| A | Contexto P2P, motivação, dados | ~5 min |
| B | Conceitos preliminares: distância, MST, Louvain/modularidade, ROC/AUC | ~7 min |
| C | Método formal (pipeline) + resultados (Figura 1 e Tabela 2) | ~6 min |
| D | Análise crítica + contribuição própria + slide de IA | ~7 min |
