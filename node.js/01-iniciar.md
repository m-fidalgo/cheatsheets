<h1 align="center">Iniciar</h1>

<h3>Básico</h3>
<p>Na pasta do projeto</p>

```
npm init -y
```
<h3>Com TypeScript</h3>
<p>Iniciar</p>

```
npm i -D typescript
npm i -D @types/node
```
<p>Criar tsconfig.json</p>

```
npx tsc --init

ou com opções

npx tsc --init --rootDir src --outDir build \ --esModuleInterop --resolveJsonModule --lib es6 \ --module commonjs --allowJs true --noImplicitAny true
```
<p>Arquivo gerado:</p>

```
{
  "compilerOptions": {
    "target": "es2016" /* Set the JavaScript language version for emitted JavaScript and include compatible library declarations. */,
    "lib": ["es6"] /* Specify a set of bundled library declaration files that describe the target runtime environment. */,
    "module": "commonjs" /* Specify what module code is generated. */,
    "rootDir": "src" /* Specify the root folder within your source files. */,
    "resolveJsonModule": true /* Enable importing .json files */,
    "allowJs": true /* Allow JavaScript files to be a part of your program. Use the `checkJS` option to get errors from these files. */,
    "outDir": "build" /* Specify an output folder for all emitted files. */,
    "esModuleInterop": true /* Emit additional JavaScript to ease support for importing CommonJS modules. This enables `allowSyntheticDefaultImports` for type compatibility. */,
    "forceConsistentCasingInFileNames": true /* Ensure that casing is correct in imports. */,
    "strict": true /* Enable all strict type-checking options. */,
    "noImplicitAny": true /* Enable error reporting for expressions and declarations with an implied `any` type.. */,
    "skipLibCheck": true /* Skip type checking all .d.ts files. */
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
