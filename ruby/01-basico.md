<h1 align="center">Básico</h1>

<h3>Sobre</h3>
<p>É uma linguagem orientada a objetos, interpretada e dinâmica</p>
<p>Seus operadores são syntactic sugars para métodos<p>
<p>Uso de snake_case</p>
 
<h3>Gemfile</h3>
<p>Arquivo que especifica as gem dependencies do projeto</p>
<p>Instalar todos os gems: <b>bundle install</b></p>
<p>Update um único gem: <b>bundle update <nome_gem></b></p>
<p>Update todos os gems <b>bundle update</b></p>

<h3>Comentários</h3>

```
# single line comment

=begin
multiline
comment
=end
```
<h3>Variáveis e Escopo</h3>
<p>O nome da variável determina seu escopo</p>
<p>Variáveis de instância e globais são <b>nil</b> até terem um valor atribuído a elas. Os demais tipos devem ser inicializados</p>
<ul>
  <li>x - variável local</li>
  <li>X - constante</li>
  <li>$x - variável global</li>
  <li>@x - variável de instância (atributos de uma classe - estado do objeto)</li>
  <li>@@x - variável de classe (estado da classe), pode ser acessada por ClassName.class_variable</li>
</ul>
<p>Verificar o escopo de uma variável x</p>

```
defined? x
```
<h3>Tipos de Dados</h3>
<p>Boolean, Numbers, String, Hashes, Arrays, Symbols</p>
<p>Verificar o tipo de uma variável a</p>

```
a.kind_of? Integer
# true ou false

a.is_a? Integer
# true ou false
```
