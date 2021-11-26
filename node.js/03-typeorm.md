<h1 align="center">TypeORM</h1>

<h3>Instalar</h3>

```
npm i typeorm
```
<h3>Package.json</h3>
<p>Adicionar script</p>

```
"scripts": {
  "typeorm": "ts-node-dev ./node_modules/typeorm/cli.js"
}
```
<h3>Arquivo ormconfig.json</h3>

```
{
  "type": "postgres",
  "host": "localhost",
  "port": "5432",
  "username": "user",
  "password": "senha",
  "database": "nomebanco",
  "migrations": ["./src/database/migrations/*.ts"],
  "entities": ["./src/models/*.ts"],
  "cli": {
    "migrationsDir": "./src/database/migrations"
  }
}

```
<h3>Arquivo connection</h3>
<p>Criar a conexão</p>

```
import { createConnection } from 'typeorm';

createConnection();
```
<p>Importar em app.js</p>

```
import './database/connection';
```
<h3>Comando - Criar Migration</h3>

```
npm run typeorm migration:create -n <nome da tabela>
```
