<h1 align="center">Iniciar</h1>

<h3>Básico</h3>
<p>Na pasta do projeto</p>

```
npm init -y
```
<h3>Com TypeScript</h3>
<p>Iniciar</p>

```
npm i typescript
npm i -D @types/node
```
<p>Criar tsconfig.json</p>

```
{
  "compilerOptions": {
    "module": "commonjs",
    "target": "es6",
    "rootDir": "./",
    "esModuleInterop": true
  }
}

```
<p>Instalar ts-node-dev</p>

```
npm i -D ts-node-dev
```
<p>No package.json: respawn faz a aplicação autualizar automaticamente após mudanças</p>

```
"scripts": {
    "start": "npx ts-node-dev --respawn app.js"
 }
```
<h3>Rodar a aplicação</h3>

```
npm run start
```

<h3>Nodemon</h3>
<p>Reinicia o servidor automaticamente após mudanças</p>

```
npm i -D nodemon
````
<p>No package.json</p>

```
"scripts": {
    "start": "nodemon app.js"
 }
```
<h3>Rodar a aplicação</h3>

```
npm run start
```
