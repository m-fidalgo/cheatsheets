<h1 align="center">Básico</h1>

<h3>Tipos de Dados</h3>
<p>char, int, float, double</p>

<h3>Modificadores</h3>
<li><b>unsigned</b> (int e char) faixa de valores positivos</li>
<li><b>signed</b> (int e char) valores positivos e negativos</li>
<li><b>long</b> (int, double) faixa de valores maior que o comum</li>
<li><b>short</b> (int) menor faixa de valores</li>

<h3>Pré-Processadores</h3>
<li><b>define</b> define um macro</li>
<li><b>undef</b> remove a definição do macro</li>
<li><b>if</b>, <b>else</b>, <b>elif</b>, <b>endif</b>: diretivas condicionais</li>

<h3>Constantes</h3>

```
#define nome valor
const tipo nome = valor;
```
<h3>Bibliotecas</h3>

```
#include <bibliotecaPadrão>
#include "blbiotecaLocal"
```
<h3>Acentuação e caracteres especiais</h3>
<p>Biblioteca <b>locale.h</b></p>

```
setlocale(LC_ALL,"");
```
<h3>Getch</h3>
<p>Biblioteca <b>conio.h</b></p>
<p>Função que pausa o terminal</p>
