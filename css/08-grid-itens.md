<h1 align="center">Grid - Propriedades dos Itens</h1>
<p align="center"><a href="gse">grid-_-start e grid-_-end</a> | <a href="#gcr">grid-column e grid-row</a> | <a href="#ga">grid-area</a> | <a href="#js">justify-self</a> | <a href="#as">align-self</a> |  <a href="#ps">place-self</a></p>

<h3 id="gse">grid-_-start e grid-_-end</h3>
<p>Determina a localização do item</p>

```
grid-column-start: <number> | <name> | span <number> | span <name> | auto;
grid-column-end: <number> | <name> | span <number> | span <name> | auto;
grid-row-start: <number> | <name> | span <number> | span <name> | auto;
grid-row-end: <number> | <name> | span <number> | span <name> | auto;
```
<li><b>number/name</b>: se refere ao número ou nome dado à linha/coluna</li>
<li><b>span number</b>: o item vai se espalhar por esse número de espaços do grid</li>
<li><b>span name</b>: o item vai se espalhar até encontrar esse nome</li>
<p>Exemplo</p>

```
.item-a {
  grid-column-start: 2;
  grid-column-end: five;
  grid-row-start: row1-start;
  grid-row-end: 3;
}
```
<img src="https://css-tricks.com/wp-content/uploads/2018/11/grid-column-row-start-end-01.svg" alt="Exemplo Grid Item" width="300px" />

<h3 id="gcr">grid-column e grid-row</h3>
<p>Unem grid-_-start e grid-_-end</p>

```
grid-column: <start-line> / <end-line> | <start-line> / span <value>;
grid-row: <start-line> / <end-line> | <start-line> / span <value>;
```
<p>Exemplo</p>

```
.item-c {
  grid-column: 3 / span 2;
  grid-row: third-line / 4;
}
```
<img src="https://css-tricks.com/wp-content/uploads/2018/11/grid-column-row.svg" width="300px" />

<h3 id="ga">grid-area</h3>
<p>Define o nome da área que o item ocupa</p>

<h3 id="js">justify-self</h3>
<p>Override no justify-items para um único item</p>

```
justify-self: start | end | center | stretch;
```
<h3 id="as">align-self</h3>
<p>Override no align-items para um único item</p>

```
align-self: start | end | center | stretch;
```
<h3 id="ps">place-self</h3>
<p>Une as propriedades align-self e justify-self, no formato <b>align-self / justify-self</b></p>
