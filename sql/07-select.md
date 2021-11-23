<h1 align="center">Select</h1>

<h3>Selecionar colunas específicas</h3>

```
SELECT col1, ..., coln FROM nomeTabela [WHERE condição];
```
<h3>Selecionar todas as colunas</h3>

```
SELECT * FROM nomeTabela [WHERE condição];
```
<h3>Adicionar aliases</h3>

```
SELECT col1 AS alias1, ..., coln AS aliasn FROM nomeTabela [WHERE condição];
```
<h3>Ignorar tuplas repetidas</h3>

```
SELECT DISTINCT col1, ..., coln FROM nomeTabela [WHERE condição];
```
<h3>Ordenar</h3>
<p>Padrão: ascendente</p>

```
SELECT col1, ..., coln FROM nomeTabela [WHERE condição] ORDER BY col [ASC | DESC];
```
