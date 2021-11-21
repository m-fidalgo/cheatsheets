<h1 align="center">Iterators</h1>

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
<h3>Observações</h3>
<p>Executando um Iterator é recebido um objeto iterable</p>
<p>Todo iterable pode ser trabalhado com for in/for of</p>
