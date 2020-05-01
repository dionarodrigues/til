# TypeORM is an ORM that can run in NodeJS

__Working on NodeJS applications I've found [TypeORM](https://typeorm.io/), an advanced object-relational mapping.__

> TypeORM is definitely the most mature Object Relational Mapper (ORM) available in the node.js world. Since it's written in TypeScript, it works pretty well with the Nest framework.
- [NestJS](https://docs.nestjs.com/recipes/sql-typeorm)

I'm creating a project using NodeJS API that is powered by a PostgreSQL database (docker image) for data storage and using TypeORM to make my life easier as a developer. :)

To start the adventure with this library I had to run the following command to install all necessary dependencies:

`yarn add typeorm pg reflect-metadata -D`

Next I need to create a new connection from the configuration file as you can see in this [documentation](https://github.com/typeorm/typeorm/blob/master/docs/using-ormconfig.md).

I also need to import "reflect-metadata" in the global place of my app (for example in app.ts): `import "reflect-metadata";`.

## Working with models

To work with models in TypeORM it's necessary to create [entities](https://typeorm.io/#/entities) (a class that maps to a database table).

To declare a model as an entity, I just need to add `@Entity()` [decorator](https://github.com/typeorm/typeorm/blob/master/docs/decorator-reference.md) before the declaration of the Class defining my model.

In addition to this, I should ideally have columns (and Primary Keys) in the model. To add these elements in the table I need to use `@Column()` and `@PrimaryColumn()` / `@PrimaryGeneratedColumn()` decorators. 

By making ‘id’ in ‘Cat’ as auto-generated primary key, a Cat model will look like this:

```
@Entity()
class Cat {

  @PrimaryGeneratedColumn()
  id: number;

  @Column()
  name: string;

  @Column()
  breed: string;

  @Column()
  age: string;

}
```

If the project is using [typescript](https://www.typescriptlang.org/), I need to aplly the follwing settings in `tsconfig.json` file:

```
  "strictPropertyInitialization": false,
  "experimentalDecorators": true,
  "emitDecoratorMetadata": true, 
```

Each entity must be registered in `ormconfig.json` file:

```
{
  "entities": [
    "./src/models/*.ts"
  ],
}
```


## Working with migrations

To work with [migrations](https://github.com/typeorm/typeorm/blob/master/docs/migrations.md) I need to apply the following settings to my `ormconfig.json` file:

```
{
  "migrations": [
    "./src/database/migrations/*.ts"
  ],
  "cli": {
    "migrationsDir": "./src/database/migrations"
  }
}
```

And add the following command to my `package.json` file:

`"typeorm": "ts-node-dev ./node_modules/typeorm/cli.js"`

Then I'll able to run the following commands to create and run migrations:

`yarn typeorm migration:create -n CreateAppointments`

`yarn typeorm migration:run`

More information on migrations can be found [here](https://github.com/typeorm/typeorm/blob/master/docs/migrations.md).


## Working with repositories

Each entity has its own [repository](https://github.com/typeorm/typeorm/blob/master/docs/custom-repository.md) which handles all operations with its entity. 

There are several ways how custom repositories can be created. And I can check all of them [here](https://github.com/typeorm/typeorm/blob/master/docs/custom-repository.md).

--- 

Cheers