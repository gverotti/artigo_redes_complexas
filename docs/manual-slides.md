# Manual dos slides

Os slides ficam em `slides/`, em LaTeX (Beamer). Cada um de nós edita o próprio arquivo e o GitHub gera o PDF
sozinho a cada `git push`.

## 1. Instalar (uma vez só)

1. **Git:** https://git-scm.com/download/win
2. **VS Code:** https://code.visualstudio.com
3. **MiKTeX** (o LaTeX para Windows): https://miktex.org/download
   - Na instalação, em *"Install missing packages on-the-fly"*, escolha **Yes**.
4. **Extensão LaTeX Workshop** no VS Code: abra a aba de extensões (`Ctrl+Shift+X`), procure por
   *LaTeX Workshop* (autor James Yu) e instale.

## 2. Baixar o repositório (uma vez só)

Aceite o convite do GitHub que chegou por e-mail. Depois, no terminal:

```bash
git clone https://github.com/gverotti/artigo_redes_complexas.git
```

No VS Code, abra a pasta `artigo_redes_complexas` (**File > Open Folder**). Abra sempre a pasta inteira, não um
arquivo solto, senão a compilação não funciona.

## 3. Qual arquivo é de quem

| Arquivo | Quem edita | Conteúdo |
|---|---|---|
| `slides/secoes/lucas-marin.tex` | Lucas Marin | Seções 1, 2.1 e 2.2: contexto, dados, modelos e métricas |
| `slides/secoes/giovani.tex` | Giovani | Seções 2.3, 2.4 e 2.5: distância, MST e medidas de rede |
| `slides/secoes/lucas-battisti.tex` | Lucas Battisti | Seção 3: resultados |
| `slides/secoes/gustavo-franco.tex` | Gustavo Franco | Seção 4: conclusão |
| `slides/secoes/grupo.tex` | Todos (combinando antes) | Análise crítica, contribuição, referências, slide final |
| `slides/main.tex` | Só mexemos combinando no grupo | Capa, visual e ordem dos arquivos |
| `slides/figuras/` | Todos | Imagens. Use o seu nome no arquivo: `giovani-mst.png` |

## 4. O dia a dia

1. **Antes de começar**, puxe o que os outros enviaram:
   ```bash
   git pull
   ```
2. Edite **só o seu arquivo** em `slides/secoes/`.
3. Salve (`Ctrl+S`). O VS Code compila sozinho. Para ver o PDF: `Ctrl+Alt+V`.
4. Quando terminar, envie:
   ```bash
   git add -A
   git commit -m "Atualiza slides da MST"
   git push
   ```

## 5. O PDF gerado pelo GitHub

A cada `push` que mexe em `slides/`, o GitHub compila tudo. Para baixar:

1. No repositório, abra a aba **Actions**.
2. Clique na execução mais recente de **Slides**.
3. Em **Artifacts**, baixe `slides-pdf`.

Se aparecer um **X vermelho**, a compilação falhou. Clique nela para ver o erro.

## 6. Regras para não dar conflito

- Cada um mexe **só no próprio arquivo**.
- `main.tex` e `grupo.tex`: avise no grupo antes de editar.
- Não suba o PDF (o `.gitignore` já impede).
- Sempre `git pull` antes de começar e `git push` quando terminar.

## 7. Problemas comuns

| Problema | Solução |
|---|---|
| O MiKTeX pergunta se pode instalar um pacote | Clique em **Install** |
| `git push` recusado (*rejected*) | Rode `git pull` e depois `git push` de novo |
| Conflito no `git pull` | Não apague nada; avise no grupo para resolvermos juntos |
| O PDF não atualiza | Confira se abriu a pasta inteira no VS Code e se o arquivo foi salvo |
| Erro de compilação | Veja a aba **Problems** do VS Code (`Ctrl+Shift+M`) |
