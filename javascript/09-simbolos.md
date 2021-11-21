<h1 align="center">Símbolos</h1>

<h3>Sobre</h3>
<p>São únicos e imutáveis, podendo ser usado como identificador das propriedades de objetos</p>

<h3>Declaração</h3>

```
var s = Symbol('simbolo');
```
<h3>.for()</h3>
<p>Registra o símbolo globalmente: se não existir será criado, se existir será retornado</p>

```
Symbol.for('simbolo');
```
<h3>.keyFor()</h3>
<p>Retorna a chave desse símbolo</h3>

```
Symbol.keyFor(s);
```
<h3>OBS</h3>
<p>JSON.stringify ignora todas as propriedades definidas com symbols</p>
