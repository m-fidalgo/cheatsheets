<h1 align="center">Código Assíncrono</h1>

<h3>Callbacks</h3>
<p>Funções de callback são executadas quando a anterior é finalizada</p>

<h3>Promises</h3>
<p>Forma mais organizada de lidar com código assíncrono, não podem ser canceladas</p>

```
var p = new Promise((resolve, reject) => {
  resolve();
})
.then();
```
<p>O return de um then passa como parâmetro para o próximo</p>
<p>Métodos estáticos</p>
<li><b>Promise.resolve()</b> recebe algo a ser resolvido, ou seja, executado de forma que se aguarde a resposta</li>
<li><b>Promise.race()</b> recebe um array de promises e executa o "then" quando a primeira delas é resolvida/rejeitada</li>
<li><b>Promise.all()</b> recebe um array de promises e executa o "then" apenas quando todas são resolvidas/rejeitadas</li>

<h3>Async/Await</h3>
<p>Deve-se declarar uma função como async para usar o await e esperar o retorno de uma promise antes de executar o restante</p>
<p>Funções async retornam promises</p>
