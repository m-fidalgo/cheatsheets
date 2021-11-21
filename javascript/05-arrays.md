<h1 align="center">Arrays</h1>

<h3>Sobre</h3>
<p>Contêm listas de dados ordenados (ordem de inserção) que podem ser de qualquer tipo</p>
<p>São mutáveis: podem ter itens adicionados/removidos mesmo se forem const</p>

<h3>Declaração</h3>

```
const a = [val1, val2, val3]
```
<h3>Acesso</h3>

```
a[índice];
```
<h3>.length</h3>
<p>Retorna o número de elementos</p>

<h3>Métodos</h3>
<li><b>.push(item)</b> adiciona um ou mais elementos no fim do array</li>
<li><b>.unshift(item)</b> adiciona um ou mais elementos no começo do array</li>
<li><b>.pop(item)</b> remove e retorna o último elemento do array</li>
<li><b>.shift(item)</b> remove e retorna o primeiro elemento do array</li>
<li><b>.splice(x, y)</b> remove o item com índice x, y vezes</li>
<li><b>.splice(x, 0, y)</b> insere y na posição x</li>
<li><b>.slice(indiceComeco, indiceFim)</b> retorna um array de indiceComeco a indiceFim - 1</li>
<li><b>.copyWithin(indiceInserir, indiceComeco, indiceFim)</b> substitui de indiceComeco a indiceFim - 1 com o item de indiceInserir</li>
<li><b>.fill(valor, indiceComeco, indiceFim)</b> preenche de indiceComeco a indiceFim - 1 com valor</li>
<li><b>.entries()</b> retorna iterator dos itens</li>
<li><b>.values()</b> iterator dos valores</li>
<li><b>.keys()</b> iterator das chaves</li>

<h3>Métodos com Array Functions</h3>
<li><b>.every(item => condição)</b> retorna true só se todos os elementos satisfazem a condição</li>
<li><b>.some(item => condição)</b> true se ao menos um a satisfaz</li>
<li><b>.filter(item => condição)</b> mantém no array apenas os elementos que satisfazem a condição</li>
<li><b>.find(item => condição)</b> retorna o 1º item que satisfaz a condição</li>
<li><b>.findIndex(item => condição)</b> retorna o índice do 1º item que satisfaz a condição</li>
<li><b>.reduce((acumulado, total) => acumulado + total)</b> reduz o array a um número</li>
<li><b>.sort((a, b) => a > b ? 1 : -1)</b> ordena crescentemente</li>
<li><b>.forEach(item => processamento)</b> executa o processamento para cada item</li>
<li><b>.map(item => novo)</b> executa um processamento para cada item, alterando-os</li>

<h3>Métodos Estáticos</h3>
<li><b>Array.of(elementos)</b> retorna um array dos elementos</li>
<li><b>Array.from(objetoIterable)</b> retorna um array do iterable</li>
