<h1 align="center">Básico</h1>

<h3>Tipos de Dados</h3>
<p>char, int, float, double, bool</p>
<p>Modificadores: signed, unsigned, long, short</p>

<h3>Compilar</h3>

```
g++ -o main.exe -I. main.cpp
```
<h3>Namespaces</h3>
<p>Escopos que contém objetos relacionados</p>
<p>Para acessar algo dentro de uma namespace é usado o operador de escopo (::)</p>

```
namespace nome {
  objetos
}
nome::objeto

using namespace nome;
objeto
```
<h3>Funções Inline</h3>
<p>O compilador substitui a chamada da função pelo código que ela implementa</p>

```
inline ret metodo(params) {}
```
