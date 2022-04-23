<h1 align="center">Módulos, Namespaces e Escopo</h1>

<h3>Módulos</h3>
<p>Cada arquivo representa um módulo (há também bibliotecas)</p>
<p>Importar recursos específicos</p>

```
from modulo import recurso
```
<p>Importar tudo</p>

```
import modulo
from modulo import *
```
<h3>Namespaces</h3>
<p>Implementados como dicionários (nomes são as chaves e objetos os valores)</p>
<p>Pode-se usar nomes iguais em namespaces diferentes</p>
<p>Namespace local: nomes dentro de uma função</p>
<p>Namespace global: nomes de módulos importados</p>
<p>Namespace interno: funções e exceções internas</p>

<h3>Escopos</h3>
<p>Escopo local: nomes disponíveis numa função</p>
<p>Escopo que delimita todas as funções que podem ser usadas</p>
<p>Escopo modular: nomes globais</p>
<p>Escopo externo: nomes internos</p>
