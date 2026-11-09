# Cronograma

Nosso prazo final é **quarta-feira, 02/12/2026, até as 18h**, quando entregamos os slides em PDF. As apresentações
são nos dias 03 e 04/12 e a ordem é sorteada na hora, então precisamos estar prontos desde o primeiro dia.

Vamos marcando `[x]` conforme terminamos cada tarefa.

---

## Semana 1: base (09 a 15/11)

- [ ] Reunião inicial: dividir os papéis e colocar os nomes no [README](README.md#grupo)
- [ ] Todos nós lemos o artigo inteiro
- [ ] Confirmar com a professora que o artigo foi aprovado
- [ ] Baixar o Supplementary Material e anotar o que tem nele em `data/README.md`
- [ ] Escolher a linguagem (provavelmente Python, que já usamos nas aulas)
- [ ] Escolher a ferramenta e o modelo dos slides
- [ ] Todos com acesso ao repositório (clonar e fazer um commit de teste)

## Semana 2: replicação (16 a 22/11)

Atenção: 20/11 (sexta) é feriado.

- [ ] **A:** carregar os dados, montar a matriz de distância euclidiana padronizada e a MST
- [ ] **B:** calcular grau, força e comunidades (Louvain) de cada empresa e refazer a Figura 1 (MST colorida por default)
- [ ] **C:** rodar Logit, LDA, CART e SVM com 10 divisões aleatórias de treino e teste e calcular AUC, KS, Gini e acurácia
- [ ] Meta da semana: chegar perto da Tabela 2 (AUC da Logit de 79,6 para 80,8)
- [ ] **D:** começar os slides de conceitos preliminares (MST, modularidade, curva ROC e AUC)
- [ ] Reunião no fim da semana, em que cada um explica a sua parte para os outros três

## Semana 3: contribuição e slides (23 a 29/11)

- [ ] Teste de DeLong e intervalos de confiança entre as 10 divisões
- [ ] Rede construída só com o conjunto de treino, para evitar vazamento de dados
- [ ] Louvain usando similaridade (1/d ou exp(-d)) no lugar da distância
- [ ] *Opcional:* aplicar o método na base da Bondora
- [ ] *Opcional:* trocar a MST por kNN ou por uma rede com limiar e testar outras centralidades (betweenness, PageRank)
- [ ] **27/11 (sexta): primeira versão completa dos slides**
- [ ] **28 ou 29/11: primeiro ensaio cronometrado (25 min)**

## Semana 4: fechamento (30/11 a 02/12)

- [ ] 30/11 (segunda): ajustes depois do ensaio
- [ ] 01/12 (terça): segundo ensaio, gerar o PDF e revisar tudo
- [ ] **02/12 (quarta): enviar o PDF** (nossa meta é até o meio-dia; o limite é 18h)
- [ ] 03 e 04/12: apresentação

---

## O que os slides precisam ter (pelo enunciado)

- [ ] Contextualização: problema, motivação e literatura
- [ ] Conceitos preliminares: tudo o que não vimos em aula
- [ ] Modelo ou método formal: notação, hipóteses e relação com a disciplina
- [ ] Resultados principais
- [ ] Análise crítica: limitações, hipóteses restritivas e extensões
- [ ] Nossa contribuição
- [ ] Slide final exigido pelo enunciado (seção 1.6)

## Divisão da apresentação (25 min)

| Integrante | Bloco | Tempo |
|---|---|---|
| A | Contexto P2P, motivação e dados | ~5 min |
| B | Conceitos preliminares: distância, MST, Louvain e modularidade, curva ROC e AUC | ~7 min |
| C | Método formal e resultados (Figura 1 e Tabela 2) | ~6 min |
| D | Análise crítica, nossa contribuição e slide final | ~7 min |
