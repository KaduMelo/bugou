---
name: pr-to-develop
description: Cria um Pull Request da branch de feature atual direto contra `develop` (ou outra base passada como argumento). Faz push se necessário, gera título e corpo a partir dos commits, e detecta PR pré-existente para evitar duplicata.
metadata:
  author: bugou
  type: dev-workflow
---

# Open PR → develop

Skill para abrir um Pull Request da branch atual contra `develop` (default) no
repositório `origin`. Sem perguntas extras quando a pré-flight passa: o objetivo
é executar o caminho feliz numa só invocação.

## User Input

```text
$ARGUMENTS
```

Se `$ARGUMENTS` estiver vazio, a base é `develop`. Caso contrário, use a primeira
palavra como nome da base (ex.: `/pr-to-develop staging` → base = `staging`).

## Pré-flight (BLOQUEADORA — não prosseguir se falhar)

Rode estes checks via Bash, em paralelo quando possível. Se qualquer um falhar,
**pare e reporte o motivo ao usuário com a próxima ação sugerida** — NÃO tente
mascarar (ex.: nunca rode `git stash` ou `git commit -am` automaticamente).

1. **Repo git válido**
   `git rev-parse --is-inside-work-tree` → MUST retornar `true`.

2. **Branch atual NÃO é a base nem branch protegida**
   `git symbolic-ref --short HEAD` → captura `CUR`.
   Se `CUR` ∈ {`<base>`, `main`, `master`}: erro
   "Branch atual é `<CUR>`; rode a skill a partir de uma branch de feature."

3. **Working tree limpo**
   `git status --porcelain` → MUST retornar vazio.
   Se sujo: erro "Há mudanças não commitadas. Commit ou stash antes de abrir o PR."

4. **`gh` instalado e autenticado**
   `gh auth status` → MUST sair com 0.
   Se não: erro "GitHub CLI não autenticado. Rode `gh auth login`."

5. **Base existe no `origin`**
   `git ls-remote --exit-code --heads origin <base>` → MUST sair com 0.
   Se não: erro "Branch `<base>` não existe em `origin`. Crie-a primeiro
   (`git push origin <base>` a partir do ponto de partida desejado)."

6. **Há commits à frente da base**
   `git fetch origin <base>` e depois `git rev-list --count origin/<base>..HEAD`
   → MUST ser ≥ 1.
   Se 0: erro "Nenhum commit nesta branch além de `origin/<base>`; não há PR
   a abrir."

## Execução

7. **Push da branch atual**
   - Se não há upstream: `git push -u origin <CUR>`.
   - Se há upstream e há commits locais não enviados: `git push`.
   - Se já está sincronizada: skip.
   Verifique com `git rev-parse --abbrev-ref --symbolic-full-name @{u} 2>/dev/null`.

8. **PR já existe?**
   `gh pr list --head <CUR> --base <base> --state open --json url,number --jq '.[0]'`
   → Se retornar objeto não-vazio: imprima a URL existente, marque como "PR já
   aberto" e **encerre sem criar duplicata**.

9. **Compor título**
   - Calcule número de commits novos: `N = git rev-list --count origin/<base>..HEAD`.
   - Se `N == 1`: título = subject desse commit (`git log -1 --format=%s`).
   - Se `N > 1`: título = subject do commit MAIS ANTIGO da série
     (`git log --format=%s origin/<base>..HEAD | tail -1`), que costuma
     refletir a intenção original.
   - **Cap em 70 caracteres.** Se passar, trunque até o último limite de palavra
     ≤ 67 chars e acrescente `…`. O título completo NÃO precisa ir no corpo
     (o resumo já cobre isso).

10. **Compor corpo** (HEREDOC, segue padrão do repositório)
    ```
    ## Summary
    <1-3 bullets sintetizando o conjunto de commits — você gera>

    ## Commits
    <output de `git log --reverse --format='- %s' origin/<base>..HEAD`>

    ## Test plan
    - [ ] <TODO específico de teste>
    - [ ] <TODO específico de teste>

    🤖 Generated with [Claude Code](https://claude.com/claude-code)
    ```
    - Os bullets de **Summary** são síntese, não lista bruta — colapse commits
      relacionados, destaque o "porquê" quando souber, máximo 3 itens.
    - **Test plan**: itens acionáveis para o reviewer testar manualmente.
      Default sensato: 1 item de "caminho feliz" + 1 item de regressão da
      área tocada. Não invente testes que você não consegue justificar
      olhando o diff.
    - Se a branch tiver spec correspondente em `specs/<branch>/spec.md`
      (Spec Kit), inclua um link relativo no topo do Summary:
      `> Spec: [specs/<branch>/spec.md](../specs/<branch>/spec.md)`.

11. **Criar o PR**
    Use HEREDOC `cat <<'EOF'` para passar o body com formatação preservada:
    ```bash
    gh pr create --base <base> --head <CUR> --title "<TITULO>" --body "$(cat <<'EOF'
    <CORPO>
    EOF
    )"
    ```
    Captura a URL retornada.

12. **Reportar ao usuário**
    Saída final em 2 linhas no máximo:
    - Linha 1: `PR aberto: <URL>`
    - Linha 2 (opcional): número de commits incluídos.
    Nada de "Resumo do que fiz", nada de re-listar o body.

## Bugou Constitution touchpoints

- **P-VI (Code Quality)**: O PR é o ponto onde revisão por par é executada;
  esta skill não substitui a revisão — apenas a habilita.
- **P-VII (Testing Standards)**: Se o diff toca caminho do dinheiro (checkout,
  Pix, entrega digital), anti-fraude, moderação ou invariantes de dados, e
  você não vê tasks/arquivos de teste correspondentes no diff, **inclua um
  item explícito no Test plan apontando o gap** — não bloqueie a abertura
  do PR, mas torne o gap visível para o reviewer.

## O que esta skill NÃO faz

- Não cria a base `develop` se ela não existe. (Decisão deliberada: criar
  branches remotas tem blast radius alto; o usuário decide.)
- Não merges nem aprova o PR.
- Não commita ou stasha mudanças pendentes — exige árvore limpa.
- Não roda CI localmente — assume que o pipeline configurado no repo cuidará.
- Não atualiza a branch contra a base (`rebase`/`merge`). Se o reviewer pedir,
  faça em comando separado e re-push.
