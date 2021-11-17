<h1 align="center">Merge e Rebase</h1>

Fundir a branch no HEAD

```
git merge <branch>
```
Usar a mergetool para resolver conflitos

```
git mergetool
```
Rebase o HEAD em branch

```
git rebase <branch>
```
Abortar o rebase

```
git rebase --abprt
```
Continuar o rebase após resolver conflitos

```
git rebase --continue
```
Resolver conflitos manualmente e marcar o arquivo como resolvido

```
git add <resolvedFile>
git rm <resolvedFile>
```
