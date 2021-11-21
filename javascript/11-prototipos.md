<h1 align="center">Protótipos</h1>

<h3>Sobre</h3>
<p>Funções construtoras a partir das quais os objetos são criados, sendo instâncias dos protótipos, herdando suas propriedades e métodos</p>

<h3>Exemplo</h3>

```
function Prototipo(a) {
  this.a = a;
  this.funcao = function() {};
}

var objeto = new Prototipo(valor);
```
<h3>Atributo Prototype</h3>
<p>Todo objeto possui o atributo <b>prototype</b>, a partir do qual é possível inserir novas propriedades/métodos no protótipo do objeto, que aparecerão em todas as suas instâncias</p>

```
objeto.prototype.novaPropriedade = valor;
```
<h3>Herança</h3>
<p>Tendo dois protótipos Prot e SubProt, pode-se indicar que SubProt é um Prot, fazendo suas instâncias terem acesso a todas as propriedades e métodos de Prot</p>

```
SubProt.prototype = new Prot();
```
