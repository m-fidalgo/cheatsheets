<h1 align="center">Kivy</h1>

<h3>Sobre</h3>
<p>Biblioteca para criar interfaces gráficas que possam ser executadas em qualquer dispositivo</p>
<p>Arquitetura dividida em módulos: instalado com pip</p>

<h3>Interface Principal</h3>
<p>Classe que deve herdar de App (importar de kivy.app) e sobrescrever o método build (que inicializa a aplicação)</p>
<p>Para invocar o build e inicializar a aplicação: <b>Nome().run()</b></p>

<h3>Widgets</h3>
<p>Importados de kivy.uix.nome</p>
<p>Ex: Button(text="Texto")</p>
<p>Linguagem kv: de "marcação", define os widgets. Cada aquivo .kv deve ser relacionado a um .py de mesmo nome</p>
<p>Nesse arquivo .py deve-se criar uma classe com o mesmo nome da tag do .kv</p>
<p>Na classe que herda de App, deve-se retornar classeDaTag() no build</p>

```
<Main>:
  Label:
    text: 'Texto'
    font_size: 50
  Button:
    text: 'Texto'
```
<h3>Eventos</h3>
<p>Alterações no estado de widgets se dão após eventos: disparados após eventos de entrada e despachados pelo EventDispatcher</p>
<p>Pontos de interações: widgets podem "escutar" estados de outros, "reagindo" a mudanças de propriedades (padrão Observer)</p>

<h3>Widgets Reativos</h3>
<p>Pode-se efetuar algo diretamente no evento do widget ou invocar métodos da classe do nome da tag (root)</p>
<p>Pode-se acessar propriedades definidas nessa classe (de kivy.properties), que podem ser alteradas em seus métodos</p>

```
Button:
  id: btn
  text: root.texto
  on_press: btn.text = 'OK'
  on_release: root.method()
```
<h3>Layouts</h3>
<p>A classe relacionada à tag do .kv herda de kivy.uix.nomeLayout</p>
<p><b>BoxLayout</b>: propriedade orientation (vertical - tudo na mesma coluna e horizontal - tudo na mesma linha)</p>
<p><b>FloatLayout</b>: deixa os elementos empilhados. É preciso definir a posição de cada um. Propriedades size_hint (tamanho vertical, horizontal) e pos_hint ({"x": pos, "top": pos})</p>
<p><b>GridLayout</b>: pode-se definir número e tamanho de linhas e colunas. Propriedades rows, cols, row_default_height (exige um row_force_default: true), col_default_width (force default true)</p>
<p><b>StackLayout</b>: empilha conforme a ordem passada. Deve-se definir o tamanho de cada widget. Propriedade orientatio (ex: 'lr-bt' -> left-right, bottom-top)</p>
