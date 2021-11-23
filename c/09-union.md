<h1 align="center">Union</h1>

<h3>Definição</h3>
<p>Parecido com struct, mas todos os campos compartilham a mesma área de armazenamento, sendo mutuamente exclusivos: só é possível usar um campo por vez</p>

<h3>Declaração</h3>

```
typedef union u_nome {
  tipo var1;
  tipo var2;
} nome;
nome var;
```
<h3>Atribuição</h3>

```
var.campo = valor;
```
