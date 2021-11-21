<h1 align="center">Flexbox - Propriedades dos Itens</h1>
<p align="center"><a href="#order">order</a> | <a href="#fg">flex-grow</a> | <a href="#fs">flex-shrink</a> | <a href="#fb">flex-basis</a> | <a href="#flex">flex</a> | <a href="#as">align-self</a></p>

<h3 id="order">order</h3>
<p>Os itens são colocados de acordo com a ordem.</p>
<p>Recebe um valor sem unidade. O padrão é 0.</p>
<p>Itens com o mesmo valor em order são colocados de acordo com a ordem do código.</p>
<img src="https://css-tricks.com/wp-content/uploads/2018/10/order.svg" alt="Order" width="250px" />

<h3 id="fg">flex-grow</h3>
<p>Define a habilidade do item crescer.</p>
<p>Recebe um valor sem unidade que serve de proporção.</p>
<img src="https://css-tricks.com/wp-content/uploads/2018/10/flex-grow.svg" alt="Flex-Grow" height="150px" />

<h3 id="fs">flex-shrink</h3>
<p>Define a habilidade do item ser reduzido.</p>
<p>Recebe um valor sem unidade que serve de proporção.</p>

<h3 id="fb">flex-basis</h3>
<p>Define o valor padrão de um elemento antes da distribuição do espaço restante.</p>
<p>Recebe um comprimento ou <b>auto</b> (padrão): verifica o width e height</p>
  
<h3 id="flex">flex</h3>
<p>Combina flex-grow, flex-shrink e flex-basis: padrão 0 1 auto</p>

<h3 id="as">align-self</h3>
<p>Dá override no align-items para um item em particular</p>
<img src="https://css-tricks.com/wp-content/uploads/2018/10/align-self.svg" alt="Align-Self" height="150px" />

```
align-self: auto | flex-start | flex-end | center | baseline | stretch;
```
