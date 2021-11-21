<h1 align="center">Generators</h1>

<h3>Sobre</h3>
<p>Funções que podem ser "pausadas" em certa linha e, quando chamadas novamente, continuam dessa mesma linha</p>

<h3>Declaração</h3>

```
function *gen() {} 
//ou
function* gen() {}

var generator = gen()
```
<h3>Yield</h3>
<p>Palavra chave que faz um valor ser retornado, pausando a função</p>

```
yield valor;
```
<p>Pode-se retornar um item de um array a cada yield</p>

```
yield* [1, 2, 3];
```
<p>O valor do yield é obtido com</p>

```
gen.next();
```

<h3>Next</h3>
<p>Na primeira vez que é executado, retorna o valor do primeiro yield</p>
<p>Ao ser executado novamente, a função gen continua até um novo yield ser encontrado</p>
