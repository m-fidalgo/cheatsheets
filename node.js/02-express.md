<h1 align="center">Express</h1>

<h3>Sobre</h3>
<p>Framework para Node.js - desenvolver aplicações back-end</p>

<h3>Instalar</h3>

```
npm i express
```
<h3>TypeScript</h3>
<p>Necessário adicionar os tipos</p>

```
npm i -D @types/express
```
<h3>Criando um server</h3>
<p>app.js/ts</p>

```
const port = 3333;
const express = require('express');
const app = express();

//converte os dados da requisição para json
app.use(express.json());

app.listen(port);
```
