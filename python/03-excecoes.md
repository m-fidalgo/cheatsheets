<h1 align="center">Exceções</h1>

<h3>Try/except</h3>
<p>Tenta executar o bloco de código e, se gerar erro, executa o código do except</p>
<p>Pode-se definir o tipo da exceção (várias pré-definidas): except nomeExceção ou atribuí-la a uma variável: except nomeExceção as e</p>

<h3>Finally</h3>
<p>Depois do try/except, código que é executado independentemente de haver erro: após o try ou após o except</p>

<h3>Raise</h3>
<p>Gerar exceção: raise exceção</p>

<h3>Assert</h3>
<p>Gerar exceção caso uma condição seja falsa: assert condição</p>
```
try:
  código
except:
  código
finally:
  código
```
