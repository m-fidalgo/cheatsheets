<h1 align="center">Objetos</h1>

<h3>Sobre</h3>
<p>Armazenam dados em pares chave-valor de forma desordenada, aceitando qualquer tipo como valor</p>
<p>São referenciados: dadas duas variáveis referenciando o mesmo objeto, alterações em uma serão refletidas na outra. Quando são passados como parâmetros o mesmo é válido</p>
<p>São mutáveis: suas propriedades podem ser mudadas mesmo se forem const</p>
<p>Comparações só retornam true quando o objeto em si é o mesmo</p>

<h3>Declaração</h3>

```
const objeto = {
  key1: 'valor1',
  key2: 'valor2',
  metodo1(param) {
    processamento
  }
};
```
<h3>Acesso</h3>

```
objeto.key1;  ou  objeto["key1"];
``` 
<h3>Desestruturação</h3>
<p>Dado um objeto com as propriedades a, b, c, é possível atribuir todas a variáveis de uma só vez</p>
  
```
const {a, b, c} = objeto;
```
<h3>Remover Propriedades</h3>
<p>Remove o valor e a própria propriedade do objeto</p>

```
delete objeto.key;  ou  delete objeto["key"];
```
<h3>Funções Estáticas</h3>
<li><b>Object.keys(obj)</b> retorna um array com os nomes das propriedades desse objeto</li>
<li><b>Object.values(obj)</b> retorna um array com os valores das propriedades do objeto</li>
<li><b>Object.seal(obj)</b> impede a criação/remoção de propriedades</li>
<li><b>Object.freeze(obj)</b> como o seal, mas também impede que propriedades sejam alteradas</li>
<li><b>Object.setPrototypeOf(child, parent)</b> atribui um protótipo parent a um objeto child</li>
<li><b>Object.assign(objAlvo, objsOrigem)</b> copia os valores de todas as propriedades dos objsOrigem para o objAlvo. O objeto alvo pode ser {} (objeto vazio): um novo é criado</li>
