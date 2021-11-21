<h1 align="center">Funções</h1>

<h3>Definição e Chamada</h3>
<p>Pode-se definir um valor padrão para um parâmetro com param = valor;

```
function nome(param) {
  return retorno;
}

nome(param);
```
<h3>Funções Anônimas</h3>
<p>Não possuem nome</p>

```
const nome = function() {
  return retorno;
}
```
<h3>Funções Autoexecutáveis</h3>
<p>Executadas no momento da declaração, podem ser anônimas</p>
<p>Criam um novo escopo</p>

```
(function nome(param) { processamento })
```
<h3>Arrow Functions</h3>
<p>Novidade do ES6, não requerem a keyword function</p>
<p>Quando só há um parâmetro não precisa de () e quando só há uma linha não requer {} nem return</p>
<p>Herda o escopo anterior</p>

```
const f = param => retorno;
```
