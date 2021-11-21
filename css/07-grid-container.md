<h1 align="center">Grid - Propriedades do Container</h1>
<p align="center"><a href="#display">display</a> | <a href="#gt">grid-template</a> | <a href="#gap">gap</a> | <a href="#ji">justify-items</a> | <a href="#ai">align-items</a> | <a href="#pi">place-items</a> | <a href="#jc">justify-content</a> | <a href="#ac">align-content</a> |  <a href="#pc">place-content</a> | <a href="#gar">grid-auto-rows</a> | <a href="#gac">grid-auto-columns</a> | <a href="#gaf">grid-auto-flow</a></p>

<h3 id="display">display</h3>
<p>Valores <b>grid</b> (para block-level grid) ou <b>inline-grid</b></p>

<h3 id="gt">grid-template</h3>
<p>Propriedades <b>grid-template-columns</b> e <b>grid-template-rows</b>: definir o número e largura das colunas e linhas. Unidade fr: útil, estabelece proporções (fração do espaço do grid)</p>
<p>Propriedade <b>grid-template-areas</b>: define o template do grid ao referenciar os grid-area definidos em cada item</p>
<p>É possível declarar tudo de uma vez com <b>grid-template</b></p>
<p>Exemplo</p>

```
grid-template-columns: repeat(4, 1fr);
grid-template-rows: auto;
//ou
grid-template: auto / repeat(4, 1fr);
grid-template-areas: 
    "header header header header"
    "main main . sidebar"
    "footer footer footer footer";
```
<img src="https://css-tricks.com/wp-content/uploads/2018/11/dddgrid-template-areas.svg" alt="Exemplo Grid Template" width="300px" />

<h3 id="gap">gap</h3>
<p>Une as propriedades <b>column-gap</b> e <b>row-gap</b> na forma <b>row-gap column-gap</b></p>
<p>Exemplo</p>

```
gap: 15px 10px;
```
<img src="https://css-tricks.com/wp-content/uploads/2018/11/dddgrid-gap.svg" alt="Exemplo Grid Gap" width="300px" />

<h3 id="ji">justify-items</h3>
<p>Alinha os itens do grid ao longo do eixo da linha</p>

```
justify-items: start | end | center | stretch;
```
<li><b>stretch</b> (<i>padrão</i>): itens esticados de forma a ocuparem toda a largura da célula</li>
<li><b>start</b>: itens na borda inicial de sua célula (esquerda)</li>
<li><b>end</b>: itens na borda final de sua célula (direita)</li>
<li><b>center</b>: itens alinhados no meio de sua célula</li>

<h3 id="ai">align-items</h3>
<p>Alinha os itens do grid ao longo do block axis (eixo da coluna)</p>

```
align-items: start | end | center | stretch;
```
<li><b>stretch</b> (<i>padrão</i>): estica os itens de forma a ocuparem toda a altura da célula</li>
<li><b>start</b>: itens na borda inicial da célula (topo)</li>
<li><b>end</b>: itens na borda final da célula</li>
<li><b>center</b>: itens centralizados na célula</li>
<li><b>baseline</b>: itens alinhados ao longo do text baseline</li>

<h3 id="pi">place-items</h3>
<p>Define <b>align-items</b> e <b>justify-items</b> ao mesmo tempo na forma <b>align-items / justify-items</b></p>

<h3 id="jc">justify-content</h3>
<p>Alinha o próprio grid dentro de seu container, horizontalmente</p>

```
justify-content: start | end | center | stretch | space-around | space-between | space-evenly;    
```
<h3 id="ac">align-content</h3>
<p>Alinha o próprio grid dentro de seu container, verticalmente</p>

```
align-content: start | end | center | stretch | space-around | space-between | space-evenly;    
```
<h3 id="pc">place-content</h3>
<p>Une as propriedades na forma <b>align-content / justify-content</b></p>

<h3 id="gar">grid-auto-rows</h3>
<p>Define o tamanho das linhas auto-geradas do grid</p>

<h3 id="gac">grid-auto-columns</h3>
<p>Define o tamanho das colunas auto-geradas do grid</p>

<h3 id="gaf">grid-auto-flow</h3>
<p>Controla o posicionamento automático de itens no grid</p>

```
grid-auto-flow: row | column | row dense | column dense;
```
<li><b>row</b> (<i>padrão</i>): o preenchimento automático se dará linha a linha, acrescentando mais se preciso</li>
<li><b>column</b>: o preenchimento será feito coluna a coluna</li>
<li><b>dense</b>: o preenchimento automático tentará preencher lacunas antes se objetos menores vierem depois. Pode deixar os itens fora de ordem</li>
