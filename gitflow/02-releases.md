<h1 align="center">Releases</h1>

Criar release (nomes no padrão x.x.x)

```
git flow release start <release> <commit>
```
Publicar no repositório remoto

```
git flow release publish <release>
```
Finalizar a release (merge em develop e master, criando uma tag)

```
git flow release finish <release>
```
