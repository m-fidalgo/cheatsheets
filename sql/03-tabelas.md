<h1 align="center">Tabelas</h1>

<h3>Criar tabela</h3>

```
CREATE TABLE nome (
  col tipo [restrições],
  ...
  col tipo [restrições]
);
```
<h3>Ver a estrutura da tabela</h3>

```
DESC nome;
```
<h3>Apagar tabela</h3>

```
DROP TABLE nome;
```
<h3>Alterar tabela</h3>

```
ALTER TABLE nome ADD col tipo;
ALTER TABLE nome ALTER COLUMN col tipo;
ALTER TABLE nome DROP COLUMN col;
```
