<h1 align="center">Iterators</h1>

<h3>Sobre</h3>
<p>Executando um Iterator é recebido um objeto iterable (pode ser trabalhado com for in/for of)</p>
<p>Objeto que acessa cada item de uma coleção por vez</p>
<p>O método next retorna o "value" (valor seguinte, vazio no fim da lista) e "done" (indica se a lista já acabou)</p>

<h3>Criação</h3>

```
var nome = {
  [Symbol.iterator]() {
    return {
      [Symbol.iterator]() {
        return this;
      },

      next() {
        return { value: valor, done: false };
      }
    };
  }
};
```
<h3>Uso</h3>

```
var a = nome[Symbol.iterator]();
a.next()
```
