<h1 align='center'>Arquivos</h1>

<h3>Abrir</h3>
<p>Cria (se não existe) e abre um arquivo</p>

```
file = open(nome, modo)
```
<p>Modos</p>
<ul>
  <li><b>'r'</b> leitura</li>
  <li><b>'w'</b> escrita (sobrescreve)</li>
  <li><b>'x'</b> escrita (dá erro se o arquivo já existir)</li>
  <li><b>'a'</b> escrita (append)</li>
  <li><b>'b'</b> binário</li>
  <li><b>'t'</b> texto</li>
  <li><b>'+'</b> atualizar</li>
</ul>

<h3>Escrita</h3>

```
file.write(string)
file.writelines(string)
```

<h3>Leitura</h3>
<p>Método readlines</p>

<h3>Fechar</h3>

```
file.close()
```
<h3>Uso do With</h3>

```
try:
  with open(nome, 'r') as file:
    linhas = file.readlines()
    for l in linhas:
      dados = l.split('-')
      print(dados[0], dados[1])
except FileNotFoundError:
  print('Não encontrado')
```
