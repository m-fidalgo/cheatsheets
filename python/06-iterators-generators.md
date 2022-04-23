<h1 align="center">Iterators e Generators</h1>

<h3>Iterators</h3>
<p>Objetos que permitem que uma coleção seja percorrida</p>
<p>Objetos iterable implementam os métodos <b>__iter__()</b> e <b>__next__()</b></p>
<ul>
  <li><b>__iter__()</b> inicializa e retorna o objeto a ser iterado</li>
  <li><b>__next__()</b> retorna o próximo elemento da sequência</li>
</ul>
<p>Criar iterator: sobrescrever __iter__() e __next__()</p>

```
iterator = iter(lista)

while true:
  try:
    elem = next(iterator)
  except StopIteration:
    break
```
<h3>Generators</h3>
<p>Forma mais simplificada de iterators</p>
<p><b>yield</b>: usado para pegar o próximo elemento</p>
<p>Precisa-se criar uma estrutura de repetição para percorrê-lo</p>
