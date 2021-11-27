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
<h3>Models</h3>
<p>Modelos para criação de tabelas</p>
<p>Exemplo</p>

```
import { Column, Entity, PrimaryGeneratedColumn } from 'typeorm';

@Entity('user')
export default class User {
  @PrimaryGeneratedColumn('increment')
  id: number;

  @Column()
  name: string;
}

```
<p>Criar Migrations: criar no banco o que foi definido nos models</p>

```
npx typeorm migration:create -n migration
```
<h3>Views</h3>
<p>Controla o modo como o cliente recebe as informações</p>
<p>Exemplo</p>

```
import User from '../models/User';

export default {
  render(user: User) {
    return {
      id: user.id,
      name: user.name,
    };
  },

  renderMany(users: User[]) {
    return users.map((user) => this.render(user));
  },
};

```
<h3>Controllers</h3>
<p>Processam o request, retornando uma response</p>
<p>Exemplo</p>

```
import { Request, Response } from "express";
import { getRepository } from "typeorm";

import User from "../models/User";
import userView from "../views/users_view";

export default {
   async index(request: Request, response: Response) {
    const usersRepository = getRepository(User);

    const users = await usersRepository.find();

    return response.json(userView.renderMany(users));
  },
  
   async show(request: Request, response: Response) {
    const { id } = request.params;

    const usersRepository = getRepository(User);

    const user = await usersRepository.findOneOrFail(id);

    return response.json(userView.render(user));
  },
  
  async create(request: Request, response: Response) {
    const {name, age} = request.body;
    const data = {name, age};
    
    const usersRepository= getRepository(User);
    
    const user = usersRepository.create(data);
    
    await usersRepository.save(user);

    return response.status(201).json(user);
}
```
