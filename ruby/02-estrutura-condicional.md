<h1 align="center">Estruturas Condicionais</h1>

<h3>If else</h3>

```
if condição
  comando
elsif condição
  comando
else
  comando
end
```
<p>Forma curta</p>

```
comando if condição
```
<h3>Unless</h3>
<p>Equivale a um if not</p>
<p>Exemplo: unless name == "bob" equivale a if name != "bob"</p>

```
unless condição
  comando
else
  comando
end
```
<p>Forma curta</p>

```
comando unless condição
```
<h3>Estruturas Case</h3>
<p>O else é opcional (como o default)</p>

```
case var
when valor
  comando
when tipo
  comando
else
  comando
end
```
<p>Forma curta</p>

```
case var
when valor then comando
else
  comando
end
```
