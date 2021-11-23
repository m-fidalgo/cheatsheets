<h1 align="center">Keys</h1>

<h3>Primary Key</h3>
<p>Torna a coluna UNIQUE e NOT NULL</p>

```
col tipo PRIMARY KEY,

ou

PRIMARY KEY (col),
```
<h3>Foreign Key</h3>

```
col tipo FOREIGN KEY REFERENCES outraTabela(colOutraTabela),

ou

FOREIGN KEY (colTabelaAtual) REFERENCES outraTabela(colOutraTabela),
```
