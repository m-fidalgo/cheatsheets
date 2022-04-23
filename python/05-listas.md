<h1 align="center">Listas</h1>

<h3>Sobre</h3>
<p>Estrutura de dados representada como uma sequência de objetos separados por vírgula, podendo armazenar qualquer tipo de dado e ser alterada a qualquer momento</p>

<h3>Declaração</h3>

```
nomeLista = [elem1, ..., elemN]
```
<h3>Métodos</h3>
<ul>
  <li><b>append(elemento)</b> insere no fim da lista</li>
  <li><b>insert(índice, elemento)</b> insere nessa posição</li>
  <li><b>remove(elemento)</b> remove o elemento</li>
  <li><b>pop(índice)</b> remove o elemento dessa posição</li>
  <li><b>index(elemento)</b> retorna o índice do elemento</li>
  <li><b>count(elemento)</b> retorna quantas vezes o elemento aparece na lista</li>
  <li><b>sort()</b> ordena a lista</li>
  <li><b>reverse()</b> inverte sua ordem</li>
  <li><b>len(lista)</b> retorna o número de itens</li>
</ul>

<h3>Deep e Shallow Copy</h3>
<p>A deep copy cria uma nova lista com o mesmo conteúdo, enquanto a shallow copy copia apenas a referência</p>

```
import copy

deepcopy = copy.deepcopy(lista)
shallowcopy = copy.copy(lista)
```
<h3>List Comprehension</h3>
<p>Forma de criar uma lista a partir de outra</p>

```
lista1 = [i for i in lista]
```
<h3>Slices</h3>
<p>Retorna outra lista</p>
<ul>
  <li><b>lista[menor:maior]</b> retorna do índice menor a maior - 1</li>
  <li><b>lista[:pos]</b> de 0 a pos - 1</li>
  <li><b>lista[pos:]</b> de pos ao fim</li>
</ul>
