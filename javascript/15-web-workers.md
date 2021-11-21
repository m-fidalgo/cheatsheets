<h1 align="center">Web Workers</h1>

<h3>Sobre</h3>
<p>Permitem que um código seja executado numa thread diferente da principal</p>
<p>Não podem acessar o DOM</p>

<h3>Arquivo worker.js</h3>
<p>Envia valores pro arquivo principal</p>

```
self.onmessage = function (message) {
  ···
}

self.postMessage({ msg: 'hello' })
```
<h3>Arquivo principal</h3>

```
var worker = new Worker('worker.js')

worker.onmessage = function (message) {
  alert(JSON.stringify(message.data))
})

worker.postMessage('hello!')
```
