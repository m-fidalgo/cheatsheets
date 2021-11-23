<h1 align="center">Constraints (Restrições)</h1>

<h3>Algumas Restrições Comuns</h3>
<li><b>NOT NULL</b>: o campo não pode ser nulo</li>
<li><b>UNIQUE</b>: o valor da coluna deve ser único entre outras tuplas</li>
<li><b>DEFAULT valor</b>: especifica um valor padrão (sobrepõe o NOT NULL)</li>
<li><b>UNSIGNED</b>: apenas valores maiores ou iguais a zero</li>
<li><b>CHECK(condição)</b>: define uma condição para a inserção</li>

<h3>Restrições de Coluna</h3>

```
col tipo NOME_CONSTRAINT,
```
<h3>Restrições de Tabela</h3>

```
CONSTRAINT nome NOME_CONSTRAINT(col1, ..., coln),
```
<h3>Ids</h3>
<li><b>MySQL</b>: a constraint AUTO_INCREMENT incrementa o valor a cada inserção</li>
<li><b>SQLServer</b>: a constraint IDENTITY(inicial, incremento) começa em inicial e adiciona incremento a cada inserção</li>
<li><b>Oracle</b>: pode-se criar uma sequence e a cada insert/no default colocar seu próximo valor ou então pode-se definir a coluna como IDENTITY (internamente usa sequence)</li>

```
col tipo GENERATED [BY DEFAULT | ALWAYS] AS IDENTITY (START WITH valor INCREMENT BY valor),
```
