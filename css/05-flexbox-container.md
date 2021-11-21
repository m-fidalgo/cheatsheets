<h1 align="center">Flexbox - Propriedades do Container</h1>
<p align="center"><a href="#display">display</a> | <a href="#fd">flex-direction</a> | <a href="#fw">flex-wrap</a> | <a href="#ff">flex-flow</a> | <a href="#jc">justify-content</a> | <a href="#ai">align-items</a> | <a href="#ac">align-content</a> | <a href="#gap">gap</a></p>

<h3 id="display">display</h3>
<p>Deve ser flex para o comportamento de flexbox</p>

<h3 id="fd">flex-direction</h3>
<img src="https://css-tricks.com/wp-content/uploads/2018/10/flex-direction.svg" alt="Flex-Direction" height="150px" />

```
flex-direction: row | row-reverse | column | column-reverse;
```
<li><b>row</b> (<i>padrão</i>): esquerda para direita</li>
<li><b>row-reverse</b>: direita para esquerda</li>
<li><b>column</b>: cima para baixo</li>
<li><b>column-reverse</b>: baixo para cima</li>

<h3 id="fw">flex-wrap</h3>
<img src="https://css-tricks.com/wp-content/uploads/2018/10/flex-wrap.svg" alt="Flex-Wrap" height="150px" />

```
flex-wrap: nowrap | wrap | wrap-reverse;
```
<li><b>nowrap</b> (<i>padrão</i>): todos os itens numa única linha</li>
<li><b>wrap</b>: os itens são quebrados em várias linhas, de cima para baixo</li>
<li><b>wrap-reverse</b>: os itens são quebrados em várias linhas, de baixo para cima</li>

<h3 id="ff">flex-flow</h3>
<p>Une as propriedades flex-direction e flex-wrap</p>

<h3 id="jc">justify-content</h3>
<img src="https://css-tricks.com/wp-content/uploads/2018/10/justify-content.svg" alt="Justify-Content" width="250px" />

```
justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
```
<li><b>flex-start</b> (<i>padrão</i>): início da direção do flex</li>
<li><b>flex-end</b>: fim da direção do flex</li>
<li><b>start</b>: início da direção do writing-mode</li>
<li><b>end</b>: fim da direção do writing-mode</li>
<li><b>left</b>: lado esquerdo do container</li>
<li><b>right</b>: lado direito do container</li>
<li><b>center</b>: itens centralizados na linha</li>
<li><b>space-between</b>: itens distribuídos de maneira igual ao longo da linha, com o primeiro item no começo e o último no final</li>
<li><b>space-around</b>: itens distribuídos igualmente ao longo da linha, com mesmo espaçamento</li>
<li><b>space-evenly</b>: itens distribuídos de modo que o espaçamento entre dois itens (e entre o primeiro/último e a borda do container) seja igual</li>
<li><b>safe</b> e <b>unsafe</b>: safe assegura que os elementos não podem ser empurrados para for da tela de forma que o conteúdo não possa ser scrolled</li>

<h3 id="ai">align-items</h3>
<img src="https://css-tricks.com/wp-content/uploads/2018/10/align-items.svg" alt="Align-Items" width="250px" />

```
align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe;
```
<li><b>stretch</b> (<i>padrão</i>): itens se esticam para preencher o container (respeitando min/max width)</li>
<li><b>flex-start/start/self-start</b>: itens no início da cross-axis</li>
<li><b>flex-end/end/self-end</b>: itens no fim da cross-axis</li>
<li><b>center</b>: itens centralizados na cross-axis</li>
<li><b>baseline</b>: itens alinhados conforme a base do texto</li>

<h3 id="ac">align-content</h3>
<p>Propriedade que só tem efeito quando há múltiplas linhas</p>
<img src="https://css-tricks.com/wp-content/uploads/2018/10/align-content.svg" alt="Align-Content" width="250px" />

```
align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
```
<li><b>normal</b> (<i>padrão</i>): itens em sua posição padrão</li>
<li><b>flex-start/start</b>: itens no início do container - flex-start considera o flex-direction e start o writing-mode</li>
<li><b>flex-end/end</b>: itens no fim do container</li>
<li><b>center</b>: itens centralizados no container</li>
<li><b>space-between</b>: itens distribuídos igualmente, com a primeira linha no começo e a última no fim do container</li>
<li><b>space-around</b>: itens distribuídos igualmente, com o mesmo espaçamento</li>
<li><b>space-evenly</b>: o espaçamento entre dois itens (itens ou iten + borda do container) é igual</li>
<li><b>stretch</b>: as linhas são esticadas de modo a preencher o container</li>

<h3 id="gap">gap</h3>
<p>Une as propriedades row-gap e column-gap, controlando o espaço entre os itens</p>
<img src="https://css-tricks.com/wp-content/uploads/2021/09/gap-1.svg" alt="Gap" width="250px" />

```
gap: row-gap column-gap;
row-gap: valor;
column-gap: valor;
```

