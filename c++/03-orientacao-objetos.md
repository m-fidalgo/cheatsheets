<h1 align="center">Orientação a Objetos</h1>

<h3>Classes e Objetos</h3>
<p>Objetos: parâmetro implícito this, referencia o próprio objeto (essa instância da classe)</p>

```
class nomeClasse {
  modAcesso:
    tipo atributo;
    tipo metodo1() {
      implementação
    }
    tipo metodo2();
}

tipo nomeClasse::metodo2() {
  implementação
}

nomeClasse obj;
nomeClasse *obj = new nomeClasse();
```
<h3>Modificadores de Acesso</h3>
<p><b>private</b>: padrão, acesso apenas pela classe atual</p>
<p><b>protected</b>: acesso pela classe atual e filhas</p>
<p><b>public</b>: acesso irrestrito</p>

<h3>Herança</h3>

```
class nomeFilha: modAcesso nomePai1, modAcesso nomePai2 {}
```
<h3>Construtores</h3>
<p>Devem ter o mesmo nome da classe, public, não podem ser sobrescritos nem ser virtual, podem sofrer sobrecarga</p>

```
class nomeClasse() {
  private:
    int valor;
  public:
    nomeClasse(int x)
      :valor(x) {}
}

class nomeClasse() {
  private:
    int x;
  public:
    nomeClasse(int _x) {
      x = _x;
    }
}
```
<h3>Destrutores</h3>
<p>Devem ter o mesmo nome da classe, precedido por ~, não podem ter retorno nem parâmetros, podem ser sobrescritos, recomenda-se que sejam virtual</p>

```
class nomeClasse {
  public:
    ~nomeClasse() {
    }
}
```
<h3>Const</h3>
<p>Objetos const não podem ser modificados</p>
<p>Métodos const são read-only: não alteram o objeto</p>
<p>Objetos const não podem chamar funções não-const</p>

<h3>Static</h3>
<p>Atributos estáticos podem ser acessados por todas as instâncias da classe</p>
<p>Métodos estáticos não tem o parâmetro implícito this nem sobrescrita</p>

<h3>Funções friend</h3>
<p>Definidas fora do escopo da classe, conseguem acessar atributos protected e private</p>

```
class nomeClasse {
  friend ret metodo(param);
  
  private:
    int x;
}

ret metodo(param) {
  implementação q pode alterar x
}
```
<h3>Funções Virtual</h3>
<p>Podem sofrer polimorfismo dinâmico (sobrescrita)</p>

```
virtual ret metodo(param);
```
<h3>Funções Pure Virtual</h3>
<p>Uma classe é abstrata se tem ao menos um método pure virtual</p>
<p>Métodos sem implementação</p>

```
virtual ret metodo(param)=0;
```
<h3>Interfaces</h3>
<p>Sem implementação explícita: classes abstratas sem construtores, destrutores, atributos e operações dinâmicas (implementadas)</p>
  
  
  
