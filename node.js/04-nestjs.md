<h1 align="center">NestJS</h1>

<h3>Sobre</h3>
<p>Framework para Node.js que usa TypeScript</p>

<h3>Iniciar</h3>

```
npm i -g @nestjs/cli
nest new nome
```
<p>É criado o diretório nome, com uma pasta src contendo os arquivos:</p>
<li><b>app.controller.ts</b>: Controller básico com uma rota</li>
<li><b>app.controller.spec.ts</b>: Testes unitários para o controller</li>
<li><b>app.module.ts</b>: Módulo raiz da aplicação</li>
<li><b>app.service.ts</b>: Service com um único método</li>
<li><b>main.ts</b>: Arquivo de entrada da aplicação</li>

<h3>Main.ts</h3>

```
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  await app.listen(3000);
}
bootstrap();
```
<h3>Rodar a aplicação</h3>

```
npm run start
```
<h3>Adicionando ConfigModule</h3>

```
npm install --save @nestjs/config
```
<p>Criar o arquivo .env na raiz da aplicação</p>

```
SERVER_PORT=3000
MODE=DEV
DB_HOST=127.0.0.1
DB_PORT=5432
DB_USERNAME=postgres
DB_PASSWORD=
DB_DATABASE=shopping_list
DB_SYNCHRONIZE=true
```
<p>Em app.module.ts</p>

```
@Module({
  imports: [ConfigModule.forRoot()],
  controllers: [AppController],
  providers: [AppService],
})
export class AppModule {}
```
<h3>Adicionando TypeORM</h3>

```
npm install --save @nestjs/typeorm typeorm
```
<p>Instalar também a biblioteca relacionada ao banco de dados usado</p>
<p>Em db.config.module.ts</p>

```import { Module } from '@nestjs/common';
import { ConfigModule } from '@nestjs/config';
import { TypeOrmModule } from '@nestjs/typeorm';
import ItemEntity from 'src/entities/item.entity';

@Module({
  imports: [
    ConfigModule.forRoot(),
    TypeOrmModule.forRoot({
      type: 'postgres',
      host: process.env.DB_HOST,
      port: parseInt(process.env.DB_PORT),
      username: process.env.DB_USERNAME,
      password: process.env.DB_PASSWORD,
      database: process.env.DB_DATABASE,
      synchronize: process.env.DB_SYNCHRONIZE === 'true',
      autoLoadEntities: true,
      migrations: ['../database/migrations/*.ts'],
      entities: ['../entities/*.ts'],
      cli: {
        migrationsDir: '../database/migrations',
      },
    }),
    TypeOrmModule.forFeature([ItemEntity]),
  ],
})
export class DbConfigModule {}

```
<p>Colocar DbConfigModule nos imports de app.module.ts</p>

<h3>Entities</h3>
<p>Definem como a entidade será representada no banco</p>
<p>Exemplo:</p>

```
import { BaseEntity, Entity, Column, PrimaryGeneratedColumn } from 'typeorm';

@Entity('users')
export default class UserEntity extends BaseEntity {
  @PrimaryGeneratedColumn('increment')
  id: number;

  @Column('varchar')
  name: string;
}

```
<p>Rodando a aplicação as entidades são criadas no banco automaticamente</p>

<h3>DTOs</h3>
<p>Data Transfer Objects</p>
<p>Instalar class-validator</p>

```
npm install --save class-validator class-transformer
```
<p>Exemplo - insert</p>

```
import { IsString, IsNotEmpty } from 'class-validator';

export default class InsertItemDto {
  @IsString()
  @IsNotEmpty()
  name: string;
}
```
<p>Exemplo - update</p>

```
import { PartialType } from '@nestjs/mapped-types';
import { CreateItemDto } from './create-item.dto';

export class UpdateItemDto extends PartialType(CreateItemDto) {}
```
<p>Usa os mesmos atributos do insert, mas torna todos opcionais</p>
<p>Mudar main.ts: adicionar a validação</p>

```
import { ValidationPipe } from '@nestjs/common';
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
 const app = await NestFactory.create(AppModule);
 app.useGlobalPipes(new ValidationPipe());
 await app.listen(3000);
}
bootstrap();
```
<h3>Providers (Services)</h3>
<p>Responsáveis pelo controle dos dados, são injetados como dependências nos controllers</p>
<p>Recebem no construtor um repositório do TypeORM de acordo com a entidade que representam</p>
<p>Exemplo</p>

```
import { Injectable, NotFoundException } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import MovieEntity from 'src/entities/movie.entity';
import InsertMovieDto from 'src/dtos/movie/insert-movie.dto';
import UpdateMovieDto from 'src/dtos/movie/update-movie.dto';

@Injectable()
export class MovieService {
  constructor(
    @InjectRepository(MovieEntity)
    private readonly repository: Repository<MovieEntity>,
  ) {}

  getAll(): Promise<MovieEntity[]> {
    return this.repository.find({ relations: ['review'] });
  }

  getOne(id: number): Promise<MovieEntity> {
    return this.repository.findOneOrFail(id, { relations: ['review'] });
  }

  insert(movieDto: InsertMovieDto): Promise<MovieEntity> {
    const movie = this.repository.create(movieDto);
    return this.repository.save(movie);
  }

  async update(id: number, movieDto: UpdateMovieDto): Promise<MovieEntity> {
    const movie = await this.repository.preload({
      id: id,
      ...movieDto,
    });

    if (!movie) throw new NotFoundException(`Movie ${id} not found`);

    return this.repository.save(movie);
  }

  async delete(id: number) {
    const movie = await this.repository.findOneOrFail(id, {
      relations: ['review'],
    });
    return this.repository.remove(movie);
  }
}
```
<h3>Controllers</h3>
<p>Lidam com requests e responses</p>

<h3>Modules</h3>
<p>Organiza providers e controllers de um mesmo tipo</p>
<p>Exemplo</p>

```
import { Module } from '@nestjs/common';
import { TypeOrmModule } from '@nestjs/typeorm';
import MovieController from 'src/controllers/movie.controller';
import MovieEntity from 'src/entities/movie.entity';
import { MovieService } from 'src/services/movie.service';

@Module({
  imports: [TypeOrmModule.forFeature([MovieEntity])],
  controllers: [MovieController],
  providers: [MovieService],
})
export default class MovieModule {}
```
<p>Em app.module.ts</p>

```
import { Module } from '@nestjs/common';
import { ConfigModule } from '@nestjs/config';
import { DbConfigModule } from './db.config.module';
import MovieModule from './movie.module';

@Module({
  imports: [ConfigModule.forRoot(), DbConfigModule, MovieModule],
})
export class AppModule {}
```
