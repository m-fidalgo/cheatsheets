<h1 align="center">Básico</h1>

<h3>Comentários</h3>
<p>// para single-line e /* */ para multi-line

<h3>Mensagens no Console</h3>

```
console.log('mensagem');
```
<h3>Operadores</h3>
<li>Aritméticos: +, -, *, /, % (módulo)</li>
<li>De Atribuição: +=, -+, *=, /=</li>
<li>De Comparação: ==. !=, ===, !===, >, >=, <, <=</li>

<h3>== e ===</h3>
<p>O operador === é chamado estritamente igual, retornando verdadeiro se os operandos forem iguais e do mesmo tipo</p>

```
x = 0
x === false  -> falso
x == false   -> verdadeiro
```
<h3>Interpolação e Concatenação de Strings</h3>
<p>Concatenando:</p>

```
'parte 1' + variável + ' parte 2'
```
<p>Interpolação: Template Literals</p>

```
`parte 1 ${variável} parte 2`
```
<h3>Módulos</h3>
<p>Exportar:</p>

```
export const a = 1;
//ou
const a = 1, b = 2;
export {a, b};
```
<p>Importar:</p>

```
import {a, b} from 'arquivo';
```
<p>Default:</p>

```
export default a;
import a from 'arquivo';
```
