<h1 align="center">Classes</h1>

<h3>Sobre</h3>
<p>Podem ser simuladas com protótipos</p>
<p>Seus métodos só podem ser acessados se forem instanciados</p>

<h3>Exemplo</h3>

```
class Classe {
  constructor(a) {
    this.a = a;
  }
  funcao() {}
};

var instancia = new Classe(a);
```
<h3>Herança</h3>
<p>Keyword <b>extends</b></p>

```
class Classe extends SuperClasse {}
```
<p>Acessar a SuperClasse: <b>super</b></p>

<h3>Métodos Estáticos</h3>
<p>Keyword <b>static</b> antes do método/propriedade. Não podem ser acessados por instâncias da classe</p>
