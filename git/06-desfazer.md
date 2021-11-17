<h1 align="center">Desfazer</h1>

Remove um arquivo do "git add"

```
git reset <file>
```
Desfaz o "git add"

```
git reset
```
Descartar todas as mudanças locais

```
git reset --hard HEAD
```
Descartar mudanças locais em um arquivo específico

```
git checkout HEAD <file>
```
Reverter um commit, gerando outro com mudanças contrárias

```
git revert <commit>
```
Redefinir HEAD para um commit anterior, descartando todas as alterações após ele

```
git reset --hard <commit>
```
Redefinir HEAD para um commit anterior, mantendo as mudanças como untracked

```
git reset <commit>
```
Redefinir HEAD para um commit anterior, mantendo as mudanças locais

```
git reset --keep <commit>
```
