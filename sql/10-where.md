<h1 align="center">Where</h1>

<h3>Operadores</h3>
<li>Condicionais: =, <>, >, >=, <, <=</li>
<li>Binários: a AND b, a OR b, NOT a</li>
<li><b>IS [NOT] NULL</b></li>
<li><b>BETWEEN</b> vê se o valor da coluna está entre uma faixa de valores: col BETWEEN menorValor AND maiorValor</li>
<li><b>IN</b> verifica se o valor está contido numa lista de valores: col IN (val1, ..., valn). Também pode receber outro select</li>
<li><b>LIKE</b> paa strings, verifica se corresponde a um padrão especificado</li>

<h3>Operadores específicos de cada BD</h3>
<li><b>MySQL</b>: REGEXP oU RLIKE como o LIKE, mas usa expressões regulares</li>

<h3>Group By e Having</h3>
<p>Agrupar informações, útil para contagens, quando funções de agregação são utilizadas</p>
<p>O having pode ser usado em conjunto para definir condições de agrupamento</p>

```
SELECT ..... GROUP BY col;
```
