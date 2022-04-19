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
import express from 'express';

const port = 3333;
const app = express();

//converte os dados da requisição para json
app.use(express.json());

app.listen(port);
```
<h3>Servidor sem express</h3>
<p>Uso do módulo HTTP do node</p>

```
const http = require('http');

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type','text/html');
  res.write('<h1>Hello World</h1>');
  res.end();
});

server.listen(3000);
```
<h3>Rotas</h3>
<p>Em routes.js</p>

```
import { Router } from 'express';

const routes = Router();

routes.get("/rota", função);

export default routes;
```
<p>App.js</p>

```
import express from 'express';
import cors from 'cors';
import routes from './routes';
import './database/connection';

const port = 3000;
const app = express();

app.use(cors());
app.use(express.json());
app.use(routes);

app.listen(port);
```
<p>CORS: middleware, instalar com npm</p>
